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