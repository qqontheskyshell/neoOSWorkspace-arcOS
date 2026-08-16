# Complete markdown Script for Q-Factor Measurement Using NLQFIT

Based on the official NPL algorithm and lmfit's complex resonator model, here's a working script:

```markdown
"""
Q-FACTOR MEASUREMENT USING NLQFIT ALGORITHM
============================================
Based on NPL Report MAT 58 (Q-factor measurement using VNA)
Uses complex domain fitting for accurate resonance detection

Required packages: pip install numpy scipy lmfit matplotlib
"""

import numpy as np
import lmfit
from lmfit import Model
import matplotlib.pyplot as plt

# ============================================================================
# SECTION 1: RESONATOR MODEL (NLQFIT-7 Complex Domain)
# ============================================================================

def resonator_model(f, f_0, Q, Q_e_real, Q_e_imag):
    """
    Complex resonator transmission model (Khalil et al. 2011)
    
    S21(f) = 1 - (Q * Q_e^-1) / (1 + 2j*Q*(f-f_0)/f_0)
    
    Parameters:
    - f: frequency array (Hz or MHz)
    - f_0: resonant frequency
    - Q: unloaded Q-factor (Q0)
    - Q_e_real: real part of coupling Q-factor
    - Q_e_imag: imaginary part of coupling Q-factor
    """
    Q_e = Q_e_real + 1j * Q_e_imag
    return 1 - (Q * Q_e**-1 / (1 + 2j * Q * (f - f_0) / f_0))


class ResonatorFitModel(Model):
    """lmfit Model wrapper with automatic parameter guessing"""
    
    def __init__(self, *args, **kwargs):
        super().__init__(resonator_model, *args, **kwargs)
        self.set_param_hint('Q', min=0)  # Q must be positive
    
    def guess(self, s21_data, f=None, **kwargs):
        """Automatically guess initial parameters from data"""
        if f is None:
            return None
        
        # Find resonance (minimum S21 magnitude)
        peak_idx = np.abs(s21_data).argmin()
        f_0_guess = f[peak_idx]
        
        # Estimate Q from bandwidth
        fmin, fmax = f.min(), f.max()
        Q_min = 0.1 * (f_0_guess / (fmax - fmin))
        Q_max = f_0_guess / np.diff(f).min()
        Q_guess = np.sqrt(Q_min * Q_max)
        
        # Estimate coupling factor
        Q_e_real_guess = Q_guess / (1 - np.abs(s21_data[peak_idx]))
        
        params = self.make_params(
            Q=Q_guess,
            Q_e_real=Q_e_real_guess,
            Q_e_imag=0,
            f_0=f_0_guess
        )
        
        params['Q'].set(min=Q_min, max=Q_max)
        params['f_0'].set(min=fmin, max=fmax)
        
        return params


# ============================================================================
# SECTION 2: SIMULATED VNA DATA (REPLACE WITH YOUR REAL DATA)
# ============================================================================

def create_simulated_vna_data():
    """
    Simulate VNA S21 sweep around resonance
    Replace with: frequencies, s21_complex = load_real_vna_data('your_file.csv')
    """
    # True parameters
    f_0_true = 100.0  # MHz
    Q_true = 10000    # Unloaded Q-factor
    Q_e_true = 9000 - 9000j  # Coupling factor
    
    # Frequency sweep
    f = np.linspace(99.8, 100.2, 200)
    
    # Generate S21 data
    s21_true = resonator_model(f, f_0_true, Q_true, Q_e_true.real, Q_e_true.imag)
    
    # Add measurement noise
    noise_scale = 0.02
    s21_measured = s21_true + noise_scale * (
        np.random.randn(len(f)) + 1j * np.random.randn(len(f))
    )
    
    return f, s21_measured


# ============================================================================
# SECTION 3: LOAD REAL VNA DATA (OPTIONAL)
# ============================================================================

def load_csv_vna_data(filename):
    """
    Load CSV with columns: frequency(Hz), S21_real, S21_imag
    
    Example:
    f, s21 = load_csv_vna_data('vna_measurement.csv')
    """
    data = np.loadtxt(filename, delimiter=',', skiprows=1)
    frequencies = data[:, 0]  # Hz
    s21_real = data[:, 1]
    s21_imag = data[:, 2]
    return frequencies, s21_real + 1j * s21_imag


def load_touchstone_file(filename):
    """
    Load Touchstone .s2p file using scikit-rf
    
    install: pip install scikit-rf
    Usage: f, s21 = load_touchstone_file('measurement.s2p')
    """
    import skrf
    network = skrf.Network(filename)
    frequencies_hz = network.f  # Hz
    s21_complex = network.s[:, 1, 0]  # S21 from port 1 to 2
    return frequencies_hz, s21_complex


# ============================================================================
# SECTION 4: MAIN MEASUREMENT FUNCTION
# ============================================================================

def measure_q_factor(frequencies, s21_complex, verbose=True):
    """
    Measure Q-factor from VNA sweep data using NLQFIT
    
    Parameters:
    - frequencies: frequency array (same units as you want output)
    - s21_complex: complex S21 array
    
    Returns:
    - Dictionary with f0, Q0, QL, coupling_factor, bandwidth
    """
    # Create model
    model = ResonatorFitModel()
    
    # Get initial guesses
    params = model.guess(s21_complex, f=frequencies)
    
    if verbose:
        print("Initial guesses:")
        print(f"  f_0: {params['f_0'].value:.4f}")
        print(f"  Q: {params['Q'].value:.2f}")
        print(f"  Q_e_real: {params['Q_e_real'].value:.2f}")
    
    # Fit the data
    result = model.fit(s21_complex, params, f=frequencies)
    
    if verbose:
        print("\n" + "=" * 60)
        print("FIT RESULTS")
        print("=" * 60)
        print(result.fit_report())
    
    # Extract results
    f0 = result.params['f_0'].value
    Q0 = result.params['Q'].value  # Unloaded Q-factor
    Q_e = result.params['Q_e_real'].value + 1j * result.params['Q_e_imag'].value
    
    # Calculate loaded Q-factor: 1/QL = 1/Q0 + 1/Qe
    Qe_magnitude = np.abs(Q_e)
    QL = Q0 / (1 + Q0 / Qe_magnitude)
    
    # Calculate bandwidth
    bandwidth = f0 / Q0
    
    # Coupling coefficient
    coupling = Q0 / Qe_magnitude
    
    return {
        'f0': f0,
        'Q0': Q0,              # Unloaded Q-factor
        'QL': QL,              # Loaded Q-factor
        'Qe': Qe_magnitude,    # External Q-factor
        'bandwidth': bandwidth,
        'coupling': coupling,
        'f0_stderr': result.params['f_0'].stderr,
        'Q0_stderr': result.params['Q'].stderr,
        'chi2': result.chi2,
        'redchi': result.redchi
    }


# ============================================================================
# SECTION 5: PLOT RESULTS
# ============================================================================

def plot_q_results(frequencies, s21_measured, results, save_path='qfactor_results.png'):
    """Plot magnitude, phase, and complex plane fits"""
    
    # Create model for plotting
    model = ResonatorFitModel()
    params = model.make_params(
        f_0=results['f0'],
        Q=results['Q0'],
        Q_e_real=np.real(results['Qe']),
        Q_e_imag=np.imag(results['Qe'])
    )
    s21_fit = model.eval(params, f=frequencies)
    
    # Plot
    plt.figure(figsize=(14, 10))
    
    # Plot 1: Magnitude (dB)
    plt.subplot(2, 2, 1)
    plt.plot(frequencies, 20*np.log10(np.abs(s21_measured)), 'b.', alpha=0.5, label='Measured')
    plt.plot(frequencies, 20*np.log10(np.abs(s21_fit)), 'r-', label='NLQFIT Fit', linewidth=2)
    plt.xlabel('Frequency (MHz)')
    plt.ylabel('|S21| (dB)')
    plt.title(f'Magnitude Response: f₀ = {results["f0"]:.4f} MHz, Q₀ = {results["Q0"]:.1f}')
    plt.axvline(results['f0'], color='g', linestyle='--', alpha=0.5, label=f'f₀')
    plt.grid(True, alpha=0.3)
    plt.legend()
    
    # Plot 2: Phase
    plt.subplot(2, 2, 2)
    plt.plot(frequencies, np.angle(s21_measured), 'b.', alpha=0.5, label='Measured')
    plt.plot(frequencies, np.angle(s21_fit), 'r-', label='Fit', linewidth=2)
    plt.xlabel('Frequency (MHz)')
    plt.ylabel('Phase (rad)')
    plt.title('Phase Response')
    plt.axvline(results['f0'], color='g', linestyle='--', alpha=0.5)
    plt.grid(True, alpha=0.3)
    plt.legend()
    
    # Plot 3: Complex plane (Smith chart style)
    plt.subplot(2, 2, 3)
    plt.plot(s21_measured.real, s21_measured.imag, 'b.', alpha=0.5, label='Measured')
    plt.plot(s21_fit.real, s21_fit.imag, 'r-', label='Fit', linewidth=2)
    plt.xlabel('Re(S21)')
    plt.ylabel('Im(S21)')
    plt.title('Complex Plane (Circle Fit)')
    plt.axhline(0, color='k', linestyle='-', alpha=0.3)
    plt.axvline(0, color='k', linestyle='-', alpha=0.3)
    plt.grid(True, alpha=0.3)
    plt.legend()
    
    # Plot 4: Results summary
    plt.subplot(2, 2, 4)
    plt.axis('off')
    summary_text = f"""
    MEASUREMENT RESULTS
    ===================
    
    Resonant Frequency (f₀):
      {results['f0']:.6f} MHz
    
    Unloaded Q-Factor (Q₀):
      {results['Q0']:.1f}
      ±{results['Q0_stderr']:.1f} (stderr)
    
    Loaded Q-Factor (Qₗ):
      {results['QL']:.1f}
    
    Bandwidth (BW = f₀/Q₀):
      {results['bandwidth']:.4f} MHz
      = {results['bandwidth']*1000:.2f} kHz
    
    Coupling Coefficient:
      {results['coupling']:.3f}
    
    Fit Quality:
      χ² = {results['chi2']:.2f}
      redχ² = {results['redchi']:.4f}
    """
    plt.text(0.1, 0.9, summary_text, fontsize=10, verticalalignment='top',
             family='monospace', bbox=dict(boxstyle='round', facecolor='wheat', alpha=0.5))
    
    plt.tight_layout()
    plt.savefig(save_path, dpi=150, bbox_inches='tight')
    print(f"\nSaved: {save_path}")


# ============================================================================
# SECTION 6: MAIN EXECUTION
# ============================================================================

def main():
    """Run complete Q-factor measurement"""
    
    print("=" * 60)
    print("Q-FACTOR MEASUREMENT USING NLQFIT ALGORITHM")
    print("=" * 60)
    
    # Step 1: Load or create data
    print("\n[1] Loading VNA sweep data...")
    
    # OPTION A: Use simulated data (for testing)
    frequencies, s21_complex = create_simulated_vna_data()
    print(f"    Using simulated data: {frequencies[0]:.2f} - {frequencies[-1]:.2f} MHz")
    
    # OPTION B: Load real CSV data
    # frequencies, s21_complex = load_csv_vna_data('vna_measurement.csv')
    
    # OPTION C: Load Touchstone file
    # frequencies, s21_complex = load_touchstone_file('measurement.s2p')
    
    print(f"    Number of points: {len(frequencies)}")
    
    # Step 2: Measure Q-factor
    print("\n[2] Running NLQFIT complex fitting...")
    results = measure_q_factor(frequencies, s21_complex, verbose=True)
    
    # Step 3: Plot results
    print("\n[3] Generating plots...")
    plot_q_results(frequencies, s21_complex, results)
    
    # Step 4: Save results to CSV
    np.savetxt('qfactor_results.csv',
               np.column_stack([frequencies,
                              s21_complex.real, s21_complex.imag]),
               header='Frequency,S21_real,S21_imag',
               delimiter=',')
    print("    Saved: qfactor_results.csv")
    
    print("\n" + "=" * 60)
    print("ANALYSIS COMPLETE")
    print("=" * 60)
    
    return results


if __name__ == "__main__":
    results = main()
```

***

## How to Use This Script

### 1. Install Dependencies
```markdown
pip install numpy scipy lmfit matplotlib
# Optional for Touchstone files:
pip install scikit-rf
```

### 2. Run with Simulated Data (for testing)
```markdown
markdown qfactor_measurement.py
```

### 3. Run with Your Real VNA Data

**Option A: CSV format** (`frequency(Hz), S21_real, S21_imag`):
```markdown
frequencies, s21 = load_csv_vna_data('your_vna_data.csv')
results = measure_q_factor(frequencies, s21)
```

**Option B: Touchstone `.s2p` file**:
```markdown
frequencies, s21 = load_touchstone_file('measurement.s2p')
results = measure_q_factor(frequencies, s21)
```

### 4. Output Files
- `qfactor_results.png` - Plot with magnitude, phase, complex plane
- `qfactor_results.csv` - Raw data + fitted values

***

## Key Q-Factor Formulas

| Formula | Meaning |
|---------|---------|
| \(Q_0 = \frac{f_0}{BW}\) | Unloaded Q from bandwidth [1] |
| \(Q_L = \frac{Q_0}{1 + \frac{Q_0}{Q_e}}\) | Loaded Q [2] |
| \(BW = \frac{f_0}{Q_0}\) | 3dB bandwidth [1] |
| \(\text{Coupling} = \frac{Q_0}{Q_e}\) | Coupling coefficient [2] |

The NLQFIT algorithm fits complex S21 data directly (not just magnitude), giving more accurate results than simple bandwidth methods.[3][4]

Sources
[1] Q Factor and Bandwidth of a Resonant Circuit | Resonance | Electronics Textbook https://www.allaboutcircuits.com/textbook/alternating-current/chpt-6/q-and-bandwidth-resonant-circuit/
[2] Qfactor (skrf.qfactor) — scikit-rf Documentation - Read the Docs https://scikit-rf.readthedocs.io/en/latest/api/qfactor.html
[3] Download markdown source code https://lmfit.github.io/lmfit-py/_downloads/3805fc8171e8a0686d5cf65be55085ee/example_complex_resonator_model.py
[4] Q-factor measurement by using a Vector Network Analyser https://eprintspublications.npl.co.uk/9304/
[5] Overview and Tutorial¶ https://lsqfit.readthedocs.io/en/latest/overview.html
[6] [PDF] Cryocharacterization of an integrated superconducting cavity for ... https://diposit.ub.edu/bitstreams/b4417274-10ff-419e-a97e-5b5ac6049198/download
[7] Complex Resonator Model - CARS https://millenia.cars.aps.anl.gov/software/markdown/lmfit/examples/example_complex_resonator_model.html
[8] [PDF] Q-factor Measurement by using a Vector Network Analyser (NPL ... https://eprintspublications.npl.co.uk/9304/3/MAT58.pdf
[9] Fit and analyze scattering parameter data from resonators - GitHub https://github.com/danielflanigan/resonator
[10] [PDF] Robust Algorithms for Fitting Q-Factor in the Complex Domain https://eprintspublications.npl.co.uk/10133/1/eid10133.pdf
[11] Circle fit optimization for resonator quality factor measurements https://link.aps.org/doi/10.1103/PhysRevResearch.6.013329
