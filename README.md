# ASP.NET Core MVC Web Application

A modern ASP.NET Core 9.0 MVC web application with Docker support.

## Prerequisites

- [.NET 9.0 SDK](https://dotnet.microsoft.com/download/dotnet/9.0)
- [Docker](https://www.docker.com/get-started) (for containerized deployment)

## Getting Started

### Running Locally

1. **Clone the repository**
   ```bash
   git clone https://github.com/atulkamble/azure-dotnet-webapp.git
   cd azure-dotnet-webapp
   ```

2. **Restore dependencies**
   ```bash
   dotnet restore
   ```

3. **Run the application**
   ```bash
   dotnet run
   ```

4. **Access the application**
   - Open your browser and navigate to: `https://localhost:5001` or `http://localhost:5000`

### Running with Docker

1. **Build the Docker image**
   ```bash
   docker build -t webapp:latest .
   ```

2. **Run the container**
   ```bash
   docker run -p 8080:8080 webapp:latest
   ```

3. **Access the application**
   - Open your browser and navigate to: `http://localhost:8080`

## Project Structure

```
├── Controllers/          # MVC Controllers
│   └── HomeController.cs
├── Models/              # Data models
│   └── ErrorViewModel.cs
├── Views/               # Razor views
│   ├── Home/
│   └── Shared/
├── wwwroot/            # Static files (CSS, JS, images)
├── Program.cs          # Application entry point
├── WebApp.csproj       # Project file
├── Dockerfile          # Docker configuration
└── .dockerignore       # Docker ignore file
```

## Docker Configuration

The application uses a multi-stage Dockerfile for optimized builds:

- **Build Stage**: Uses .NET SDK 9.0 to build the application
- **Publish Stage**: Publishes the release build
- **Runtime Stage**: Uses .NET ASP.NET Runtime 9.0 for minimal image size
- **Security**: Runs as non-root user for enhanced security
- **Port**: Exposes port 8080

## Development

### Build the project
```bash
dotnet build
```

### Run tests
```bash
dotnet test
```

### Publish for production
```bash
dotnet publish -c Release -o ./publish
```

## Environment Variables

- `ASPNETCORE_ENVIRONMENT`: Set to `Development`, `Staging`, or `Production`
- `ASPNETCORE_URLS`: Configure the URLs the app listens on (default: `http://+:8080` in Docker)

## License

This project is licensed under the MIT License.

## Author

**Atul Kamble**
- GitHub: [@atulkamble](https://github.com/atulkamble)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
