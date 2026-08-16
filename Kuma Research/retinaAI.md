Your permission block makes the module **root-private**: directories become `0700`, regular files become `0600`, and the two boot scripts become executable only by root (`0700`). The scripts can run under Magisk’s root context, but the PPM asset will not be readable by normal Android apps or most system processes if it remains `0600`.[1][2]

## Permission meaning

```sh
set_permissions() {
  set_perm_recursive "$MODPATH" 0 0 0700 0600
  set_perm "$MODPATH/post-fs-data.sh" 0 0 0700
  set_perm "$MODPATH/service.sh" 0 0 0700
}
```

| Item | Mode | Meaning |
|---|---:|---|
| Directories | `0700` | Only root can list, enter, or modify them |
| Normal files | `0600` | Only root can read or write them |
| `post-fs-data.sh` | `0700` | Only root can read, write, or execute |
| `service.sh` | `0700` | Only root can read, write, or execute |

`set_perm_recursive` applies the directory mode to directories and file mode to files recursively; the later `set_perm` calls override the script mode so they are executable.[1][2]

## PPM has no control logic

A `.ppm` is only raster image data. For a P3 PPM, the content specifies its format marker, width, height, maximum color value, and RGB samples. A `1 × 1` PPM has exactly one RGB triplet; for example, `255 255 255` is white and `0 0 0` is black.[3][4][5]

So this file:

```ppm
P3
1 1
255
255 255 255
```

is only a one-pixel white image. It cannot execute shell commands, manipulate the display, or control Android by itself.

## What each script can do

### `post-fs-data.sh`

This executes in Magisk’s early `post-fs-data` boot stage. It is blocking and runs before Zygote, so keep it very short; unsuitable work here can delay boot or cause boot problems. It can check, create, replace, delete, or change permissions on the PPM file, but it cannot make that image automatically appear on screen.[1][6]

Safe example—verify that the PPM is present and valid:

```sh
#!/system/bin/sh

MODDIR="${0%/*}"
PPM="${MODDIR}/system/media/arcos/baseframe-1px.ppm"
LOG="/data/local/tmp/baseframe-arcos-ppm.log"

if [ -r "$PPM" ] && [ "$(head -n 1 "$PPM")" = "P3" ]; then
  echo "PPM exists and has P3 header" > "$LOG"
else
  echo "PPM missing or invalid" > "$LOG"
fi
```

Use this stage for minimal **validation or filesystem preparation**, not display/UI control.

### `service.sh`

This runs later, after modules are mounted, in Magisk’s late-start service stage. It is the better place for non-critical checks, logging, and background monitoring because it does not block the core boot sequence in the same way.[1][6][7]

Safe example—detect whether the PPM changed:

```sh
#!/system/bin/sh

MODDIR="${0%/*}"
PPM="${MODDIR}/system/media/arcos/baseframe-1px.ppm"
STATE="/data/local/tmp/baseframe-arcos-ppm.sha256"

until [ "$(getprop sys.boot_completed)" = "1" ]; do
  sleep 2
done

if [ -f "$PPM" ]; then
  sha256sum "$PPM" > "$STATE"
  log -t "baseFrame@arcOS" "PPM marker present; checksum recorded"
else
  log -t "baseFrame@arcOS" "PPM marker not found"
fi
```

That script **observes** the image file. It does not manipulate pixels or draw anything.

## If you want pixel modification

A shell script can replace the PPM contents, for example switching your marker between white and black. This changes the **file**, not the physical display:

```sh
set_ppm_pixel() {
  color="$1"
  ppm="$2"

  case "$color" in
    white) rgb="255 255 255" ;;
    black) rgb="0 0 0" ;;
    red)   rgb="255 0 0" ;;
    green) rgb="0 255 0" ;;
    blue)  rgb="0 0 255" ;;
    *) return 2 ;;
  esac

  cat > "$ppm" <<EOF
P3
1 1
255
$rgb
EOF
}
```

Example use in `service.sh`:

```sh
set_ppm_pixel red "$MODDIR/system/media/arcos/baseframe-1px.ppm"
```

But with your current `0600` rule, only root can read the updated PPM. If an app, wallpaper component, or SystemUI overlay must read it, set that image to `0644` instead:

```sh
set_perm "$MODPATH/system/media/arcos/baseframe-1px.ppm" 0 0 0644
```

## Key distinction

- **File manipulation:** `post-fs-data.sh` or `service.sh` can inspect, replace, checksum, or change permissions of a PPM.
- **Image rendering:** neither script renders the PPM onto the display.
- **Display control:** requires a legitimate Android UI component—such as your own foreground app/service or wallpaper app—with the appropriate Android permissions and user-visible behavior; it is not provided by PPM or Magisk file overlay alone.

Sources
[1] Developer Guides | Magisk https://topjohnwu.github.io/Magisk/guides.html
[2] StevenBlock/customize.sh at main · Magisk-Modules-Alt-Repo/StevenBlock https://github.com/Magisk-Modules-Alt-Repo/StevenBlock/blob/main/customize.sh
[3] Portable Pixmap File Format https://oceancolor.gsfc.nasa.gov/staff/norman/seawifs_image_cookbook/faux_shuttle/ppm.html
[4] PPM - Accusoft Documentation https://help.accusoft.com/ImageGear-Net/v25.0/Windows/HTML/PPM.html
[5] PPM/PGM/PBM image files - Paul Bourke https://paulbourke.net/dataformats/ppm/
[6] Module Development | topjohnwu/Magisk | DeepWiki https://deepwiki.com/topjohnwu/Magisk/8.1-module-development
[7] 开发者指南| Magisk - E7KMbb.github.io https://e7kmbb.github.io/Magisk/guides.html
[8] Netpbm - Wikipedia https://en.wikipedia.org/wiki/Netpbm
[9] PPM Format Specification https://davis.lbl.gov/Manuals/NETPBM/doc/ppm.html
[10] hw4_1 http://www.cs.columbia.edu/~cannon/1006/handouts/hw3.pdf
[11] Magisk Module Installer Guide | PDF | Zip (File Format) https://www.scribd.com/document/901284983/aim-auper
[12] PlayIntegrityFix文件权限：module目录权限配置详解 - CSDN博客 https://blog.csdn.net/gitblog_01128/article/details/151310022
[13] Install | PDF - Scribd https://www.scribd.com/document/635606433/install
