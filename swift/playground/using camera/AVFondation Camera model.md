```swift
final class DataModel: ObservableObject {
let camera = Camera() // NSObject Class
**let** photoCollection = PhotoCollection(smartAlbum: .smartAlbumUserLibrary) // NSObject class
// ...
}
```

### Function handle preview Camera
```swift
 func handleCameraPreviews() **async** {


let imageStream = camera.previewStream
            .map { $0.image }
        for await image in imageStream {

            Task { @MainActor in
                viewfinderImage = image
            }
        }
    }
```

fungsi akan mengambil [[Camera Class]] untuk mendapatkan stream secara langsung dan menampilkan sebagai preview pada IU

### Fungsi handle Photo gallery
```swift
func handleCameraPhotos() async {

        let unpackedPhotoStream = camera.photoStream
            .compactMap { self.unpackPhoto($0) }
            
        for await photoData in unpackedPhotoStream {

            Task { @MainActor in
                thumbnailImage = photoData.thumbnailImage
            }

            savePhoto(imageData: photoData.imageData)
        }

    }
```

fungsi akan mengabil seluruh foto gallery pada device melalui class [[PhotoAsset Class]]

### Fungi unpack image file
fungsi berguna untuk melakukan proses ekstraksi/*unpack* pada data yang ditangkap oleh kamera untuk digunakan.
`DataModel.swift:82`
```swift
private func unpackPhoto(_ photo: AVCapturePhoto) -> PhotoData? {

guard let imageData = photo.fileDataRepresentation() else { return nil }
       // ...
       
        return PhotoData(thumbnailImage: thumbnailImage, thumbnailSize: thumbnailSize, imageData: imageData, imageSize: imageSize)

    }
```

### Fungsi menyimpan gambar pada penyimpanan foto
Fungsi akan melakukan proses penyimpanan foto secara *Asyncronous*, dimana akan diberikan sebuah imageData dengan tipe data `Data`
`DataModel.swift:101`
```swift
func savePhoto(imageData: Data) {
        Task {
            do {
                try await photoCollection.addImage(imageData)
                logger.debug("Added image data to photo collection.")
            } catch let error {
                logger.error("Failed to add image to photo collection: \(error.localizedDescription)")
            }
        }
    }
```