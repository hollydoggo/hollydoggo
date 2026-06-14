# Temperature Monitor

Temperature Monitor is a Windows desktop app for viewing live CPU and GPU temperature readings, fan RPM values, and a compact always-on-top overlay.

## Features

- Live CPU and GPU temperature display in Celsius
- CPU and GPU fan RPM display
- Color-coded temperature bars
- Compact overlay window for quick monitoring while using other apps
- System tray menu with overlay and exit options
- Fallback simulated readings when hardware sensors are unavailable

## Run The App

The published executable is in:

```text
publish\WinFormsApp1.exe
```

Run it from the `publish` folder so the required DLL files beside it are available.

## Use The Overlay

1. Open `WinFormsApp1.exe`.
2. Click `Show Overlay`.
3. Drag the overlay to the place you want on screen.
4. Click the overlay close button to return to the main window.

The app can also be controlled from the system tray icon.

## Build From Source

Requirements:

- Windows
- .NET 10 SDK

Build and publish:

```powershell
dotnet publish WinFormsApp1\WinFormsApp1.csproj -c Release -r win-x64 --self-contained false -p:PublishSingleFile=false -o publish
```

The executable will be created at:

```text
publish\WinFormsApp1.exe
```

## Dependencies

The app uses `LibreHardwareMonitorLib` to read hardware sensor data.

This project includes a `NuGet.config` file that points to:

- `packages`, a local package cache
- `nuget.org`, the public NuGet package source

The local package cache is useful if Windows has trouble connecting to NuGet because of certificate or TLS configuration issues.

## Notes

- Some hardware may not expose every sensor, especially fan speeds.
- When real sensor data is not available, the app falls back to estimated values so the UI still works.
- For best access to hardware sensors, run the app with normal desktop permissions; some machines may require administrator permissions for complete readings.
