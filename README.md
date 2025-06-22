# WebApiContainerDemo

## Running Visual Studio Containers with Podman on Windows

This project demonstrates running an ASP.NET Core Web API in a container using Podman as the container engine on Windows. Follow these steps to set up your environment and run the project in a container from Visual Studio:

---

## Prerequisites

- **Windows 10/11**
- **Visual Studio 2022** (with .NET and Container Development workloads)
- **Podman for Windows** ([Download here](https://podman.io/getting-started/installation))
- **Podman Desktop** (Optional)

---

## Setup Instructions

### 1. Install Podman
- Download and install Podman for Windows from the [official site](https://podman.io/getting-started/installation).
- During installation, ensure the option to set up the Podman machine is checked.
- After installation, open a terminal (PowerShell) and run:

  ```powershell
  podman machine init
  podman machine set --rootful
  podman machine start
  ```

- Confirm Podman is running:

  ```powershell
  podman info
  ```

### 2. Configure Windows to Use Podman

- Open Control Panel.
- Go to **User Accounts\User Accounts**.
- Select **Change my environment variables**.
- Set a User Environment variable `DOCKER_HOST` to `npipe:////./pipe/podman-machine-default` (matches the `DOCKER_HOST` in `launchSettings.json`).
- Set a User Environment variable `DOCKER_BUILDKIT` to `0` (may not be necessary)


### 3. Build and Run the Project

- Open the solution in Visual Studio.
- Select the `Container (Dockerfile)` profile.
- Press **F5** to build and run the project in a Podman container.
- The API will be available at the URLs specified in `launchSettings.json` (e.g., `http://localhost:8080` for HTTP, `https://localhost:8081` for HTTPS).

---

## Troubleshooting

- If you encounter issues, ensure the Podman machine is running (`podman machine start`).
- Check that the named pipe (`npipe:////./pipe/podman-machine-default`) exists and is accessible.
- Make sure Visual Studio is using the correct CLI and host settings for Podman.

---

## References

- [Podman Documentation](https://docs.podman.io/)
- [Visual Studio Container Tools](https://learn.microsoft.com/en-us/visualstudio/containers/overview)
