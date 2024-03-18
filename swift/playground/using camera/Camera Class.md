
## Fungsi `Start` 
fungsi ini yang menjadi utama class pada `Camera` sebab ini akan mumulai seluruh function kebutuhan kamera seperti meminta Izin akses kamera pada device `Camera.swift:169`.

`Camera.swift:241`
```swift
func start() async {
        let authorized = await checkAuthorization()
        guard authorized else {
            logger.error("Camera access was not authorized.")
            return
        }

        if isCaptureSessionConfigured {
            if !captureSession.isRunning {
                sessionQueue.async { [self] in
                    self.captureSession.startRunning()
                }
            }
            return
        }

        sessionQueue.async { [self] in
            if captureDevice == nil {
                captureDevice = availableCaptureDevices.first ?? AVCaptureDevice.default(for: .video)
            }
            self.configureCaptureSession { success in
                guard success else { return }
                self.captureSession.startRunning()
            }
        }
    }
```

