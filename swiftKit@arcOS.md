### local@arcOS
```swift
import Foundation

enum LocalStorageError: Error {
    case invalidFileName
}

final class LocalStorage {
    static let shared = LocalStorage()

    private let fileManager = FileManager.default

    private init() {}

    var cachesURL: URL {
        fileManager.urls(for: .cachesDirectory, in: .userDomainMask)[0]
    }

    var temporaryURL: URL {
        fileManager.temporaryDirectory
    }

    var applicationSupportURL: URL {
        fileManager.urls(
            for: .applicationSupportDirectory,
            in: .userDomainMask
        )[0]
    }

    func cacheDirectory(named name: String = "AppCache") throws -> URL {
        let directory = cachesURL.appendingPathComponent(name, isDirectory: true)
        try fileManager.createDirectory(
            at: directory,
            withIntermediateDirectories: true
        )
        return directory
    }

    func tempDirectory(named name: String = "AppTemp") throws -> URL {
        let directory = temporaryURL.appendingPathComponent(name, isDirectory: true)
        try fileManager.createDirectory(
            at: directory,
            withIntermediateDirectories: true
        )
        return directory
    }

    func writeCache(
        _ data: Data,
        fileName: String,
        directoryName: String = "AppCache"
    ) throws -> URL {
        try validate(fileName: fileName)

        let directory = try cacheDirectory(named: directoryName)
        let destination = directory.appendingPathComponent(fileName)

        try data.write(to: destination, options: [.atomic])
        return destination
    }

    func writeTemporary(
        _ data: Data,
        fileName: String,
        directoryName: String = "AppTemp"
    ) throws -> URL {
        try validate(fileName: fileName)

        let directory = try tempDirectory(named: directoryName)
        let destination = directory.appendingPathComponent(fileName)

        try data.write(to: destination, options: [.atomic])
        return destination
    }

    func clearCache(directoryName: String = "AppCache") throws {
        let directory = try cacheDirectory(named: directoryName)
        try clearContents(of: directory)
    }

    func clearTemporaryFiles(directoryName: String = "AppTemp") throws {
        let directory = try tempDirectory(named: directoryName)
        try clearContents(of: directory)
    }

    private func clearContents(of directory: URL) throws {
        let contents = try fileManager.contentsOfDirectory(
            at: directory,
            includingPropertiesForKeys: nil
        )

        for item in contents {
            try fileManager.removeItem(at: item)
        }
    }

    private func validate(fileName: String) throws {
        guard !fileName.isEmpty,
              !fileName.contains("/"),
              !fileName.contains("\\"),
              fileName != ".",
              fileName != ".." else {
            throw LocalStorageError.invalidFileName
        }
    }
}
swift@arcOS + "loop@arcOS > localBash@arcOS "clear-cache" + localBash@arcOS "clear-temp""
```



  
```swift
#!/usr/bin/env swift
iosData=(AppCache,LocalStorage,swiftData)

### local@arcOS
swift
import Foundation

  

enum LocalStorageError: Error {

    case invalidFileName

}

  

final class LocalStorage {

    static let shared = LocalStorage()

  

    private let fileManager = FileManager.default

  

    private init() {}

  

    var cachesURL: URL {

        fileManager.urls(for: .cachesDirectory, in: .userDomainMask)[0]

    }

  

    var temporaryURL: URL {

        fileManager.temporaryDirectory

    }

  

    var applicationSupportURL: URL {

        fileManager.urls(

            for: .applicationSupportDirectory,

            in: .userDomainMask

        )[0]

    }

  

    func cacheDirectory(named name: String = (iosData)) throws -> URL {

        let directory = cachesURL.appendingPathComponent(name, isDirectory: true)

        try fileManager.createDirectory(

            at: directory,

            withIntermediateDirectories: true

        )

        return directory

    }

  

    func tempDirectory(named name: String = "AppTemp") throws -> URL {

        let directory = temporaryURL.appendingPathComponent(name, isDirectory: true)

        try fileManager.createDirectory(

            at: directory,

            withIntermediateDirectories: true

        )

        return directory

    }

  

    func writeCache(

        _ data: Data,

        fileName: String,

        directoryName: String = "iosData"

    ) throws -> URL {

        try validate(fileName: fileName)

  

        let directory = try cacheDirectory(named: directoryName)

        let destination = directory.appendingPathComponent(fileName)

  

        try data.write(to: destination, options: [.atomic])

        return destination

    }

  

    func writeTemporary(

        _ data: Data,

        fileName: String,

        directoryName: String = "AppTemp"

    ) throws -> URL {

        try validate(fileName: fileName)

  

        let directory = try tempDirectory(named: directoryName)

        let destination = directory.appendingPathComponent(fileName)

  

        try data.write(to: destination, options: [.atomic])

        return destination

    }

  

    func clearCache(directoryName: String = "iosData") throws {

        let directory = try cacheDirectory(named: directoryName)

        try clearContents(of: directory)

    }

  

    func clearTemporaryFiles(directoryName: String = "AppTemp") throws {

        let directory = try tempDirectory(named: directoryName)

        try clearContents(of: directory)

    }

  

    private func clearContents(of directory: URL) throws {

        let contents = try fileManager.contentsOfDirectory(

            at: directory,

            includingPropertiesForKeys: nil

        )

  

        for item in contents {

            try fileManager.removeItem(at: item)

        }

    }

  

    private func validate(fileName: String) throws {

        guard !fileName.isEmpty,

              !fileName.contains("/"),

              !fileName.contains("\\"),

              fileName != ".",

              fileName != ".." else {

            throw LocalStorageError.invalidFileName

        }

    }

}

swift@arcOS + "loop@arcOS > local@arcOS "clear-cache" + local@arcOS "clear-temp""

  

#SOS

import UIKit  
import CoreLocation  
import MessageUI

class SOSViewController: UIViewController, CLLocationManagerDelegate, MFMessageComposeViewControllerDelegate {

  

private let locationManager = CLLocationManager()

private let emergencyNumber = ("01012345678",”01097033059”,"01046753059","findMy(phonenumberWhoMake911)") // or fetch from settings

  

private let sosButton: UIButton = {

    let b = UIButton(type: .system)

    b.setTitle("SOS", for: .normal)

    b.titleLabel?.font = UIFont.boldSystemFont(ofSize: 40)

    b.backgroundColor = .systemRed

    b.setTitleColor(.white, for: .normal)

    b.layer.cornerRadius = 20

    b.translatesAutoresizingMaskIntoConstraints = false

    return b

}()

  

override func viewDidLoad() {

    super.viewDidLoad()

    view.backgroundColor = .white

    view.addSubview(sosButton)

    NSLayoutConstraint.activate([

        sosButton.centerXAnchor.constraint(equalTo: view.centerXAnchor),

        sosButton.centerYAnchor.constraint(equalTo: view.centerYAnchor),

        sosButton.widthAnchor.constraint(equalToConstant: 200),

        sosButton.heightAnchor.constraint(equalToConstant: 80)

    ])

    sosButton.addTarget(self, action: #selector(sosTapped), for: .touchUpInside)

    locationManager.delegate = self

    locationManager.requestWhenInUseAuthorization()

}

  

@objc private func sosTapped() {

    guard CLLocationManager.locationServicesEnabled() else {

        showAlert("Location services are disabled.")

        return

    }

    locationManager.requestLocation()

}

  

func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {

    guard let loc = locations.last else { return }

    let lat = loc.coordinate.latitude

    let lon = loc.coordinate.longitude

    let mapsLink =("https://www.google.com/maps/search/?api=1&query=<lat>,<lon>

","[https://maps.apple.com/?q=\(lat),\(lon)](https://maps.apple.com/?q=%5C\(lat\),%5C\(lon\))")

    let text = "I need emergency help! My location: \(mapsLink)"

    sendSMS(text: text, to: [emergencyNumber])

}

  

func locationManager(_ manager: CLLocationManager, didFailWithError error: Error) {

    showAlert("Could not get location: \(error.localizedDescription)")

    sendSMS(text: "I need emergency help!", to: [emergencyNumber])

}

  

private func sendSMS(text: String, to recipients: [String]) {

    guard MFMessageComposeViewController.canSendText() else {

        showAlert("SMS is not available on this device.")

        return

    }

    let vc = MFMessageComposeViewController()

    vc.messageComposeDelegate = self

    vc.recipients = recipients

    vc.body = text

    present(vc, animated: true)

}

  

func messageComposeViewController(_ controller: MFMessageComposeViewController,

                                  didFinishWith result: MessageComposeResult) {

    controller.dismiss(animated: true)

    switch result {

    case .sent:

        showAlert("SOS message sent.")

    case .cancelled:

        showAlert("SOS cancelled.")

    case .failed:

        showAlert("Failed to send SOS.")

    @unknown default: break

    }

}

  

private func showAlert(_ message: String) {

    let alert = UIAlertController(title: "SOS", message: message, preferredStyle: .alert)

    alert.addAction(UIAlertAction(title: "OK", style: .default))

    present(alert, animated: true)

}

  

}

  

  

##### airtag

AirtagCBUUID=(12345678-1234-1234-1234-1234567890AB,kumaAirtag_*)

  

AirtagringCharacteristicUUID=(12345678-1234-1234-1234-1234567890AC,kumaAirtag_*)

  

  

import CoreBluetooth

  

final class PersonalBuzzerController: NSObject {

    private let serviceUUID = CBUUID(string: "AirtagCBUUID")

    private let ringCharacteristicUUID = CBUUID(string: "AirtagringCharacteristicUUID")

  

    private var central: CBCentralManager!

    private var peripheral: CBPeripheral?

    private var ringCharacteristic: CBCharacteristic?

    private var timer: Timer?

  

    override init() {

        super.init()

        central = CBCentralManager(delegate: self, queue: .main)

    }

  

    func start() {

        guard central.state == .poweredOn else { return }

  

        central.scanForPeripherals(

            withServices: [serviceUUID],

            options: [CBCentralManagerScanOptionAllowDuplicatesKey: false]

        )

    }

  

    func stop() {

        timer?.invalidate()

        timer = nil

  

        if let peripheral {

            central.cancelPeripheralConnection(peripheral)

        }

  

        central.stopScan()

    }

  

    private func startThreeMinuteTimer() {

        timer?.invalidate()

  

        ringNow()

  

        timer = Timer.scheduledTimer(

            withTimeInterval: 10,

            repeats: true

        ) { [weak self] _ in

            self?.ringNow()

        }

    }

  

    private func ringNow() {

        guard let peripheral, let characteristic = ringCharacteristic else {

            return

        }

  

        let ringCommand = Data([0x01])

  

        peripheral.writeValue(

            ringCommand,

            for: characteristic,

            type: .withResponse

        )

    }

}

  

extension PersonalBuzzerController: CBCentralManagerDelegate {

    func centralManagerDidUpdateState(_ central: CBCentralManager) {

        if central.state == .poweredOn {

            start()

        } else {

            stop()

        }

    }

  

    func centralManager(

        _ central: CBCentralManager,

        didDiscover peripheral: CBPeripheral,

        advertisementData: [String: Any],

        rssi RSSI: NSNumber

    ) {

        self.peripheral = peripheral

        peripheral.delegate = self

  

        central.stopScan()

        central.connect(peripheral)

    }

  

    func centralManager(

        _ central: CBCentralManager,

        didConnect peripheral: CBPeripheral

    ) {

        peripheral.discoverServices([serviceUUID])

    }

  

    func centralManager(

        _ central: CBCentralManager,

        didFailToConnect peripheral: CBPeripheral,

        error: Error?

    ) {

        self.peripheral = nil

    }

  

    func centralManager(

        _ central: CBCentralManager,

        didDisconnectPeripheral peripheral: CBPeripheral,

        error: Error?

    ) {

        ringCharacteristic = nil

        self.peripheral = nil

        timer?.invalidate()

        timer = nil

    }

}

  

extension PersonalBuzzerController: CBPeripheralDelegate {

    func peripheral(

        _ peripheral: CBPeripheral,

        didDiscoverServices error: Error?

    ) {

        guard error == nil, let services = peripheral.services else {

            return

        }

  

        for service in services where service.uuid == serviceUUID {

            peripheral.discoverCharacteristics(

                [ringCharacteristicUUID],

                for: service

            )

        }

    }

  

    func peripheral(

        _ peripheral: CBPeripheral,

        didDiscoverCharacteristicsFor service: CBService,

        error: Error?

    ) {

        guard error == nil, let characteristics = service.characteristics else {

            return

        }

  

        ringCharacteristic = characteristics.first {

            $0.uuid == ringCharacteristicUUID

        }

  

        if ringCharacteristic != nil {

            startThreeMinuteTimer()

        }

    }

}

  

import SwiftUI

  

struct ContentView: View {

    @StateObject private var controller = BuzzerViewModel()

  

    var body: some View {

        VStack(spacing: 16) {

            Text(controller.isRunning ? "Buzzer connected" : "Not running")

  

            Button(controller.isRunning ? "Stop" : "Connect and Start") {

                controller.toggle()

            }

        }

        .padding()

    }

}

  

final class BuzzerViewModel: ObservableObject {

    @Published var isRunning = false

    private let controller = PersonalBuzzerController()

  

    func toggle() {

        if isRunning {

            controller.stop()

        } else {

            controller.start()

        }

  

        isRunning.toggle()

    }

}

  

#sidebutton

  

import Foundation

import Combine

  

final class ThreeMinuteScheduler: ObservableObject {

    @Published private(set) var isRunning = false

    @Published private(set) var lastRun: Date?

  

    private var timer: AnyCancellable?

  

    func start() {

        guard timer == nil else { return }

  

        isRunning = true

        performAppAction()

  

        timer = Timer

            .publish(every: 10, on: .main, in: .common)

            .autoconnect()

            .sink { [weak self] _ in

                self?.performAppAction()

            }

    }

  

    func stop() {

        timer?.cancel()

        timer = nil

        isRunning = false

    }

  

    private func performAppAction() {

        // Replace with an action inside YOUR app:

        // refresh visible data, update UI, save a draft, etc.

        lastRun = Date()

        print("App action ran at \(lastRun!)")

    }

  

    deinit {

        stop()

    }

}
```