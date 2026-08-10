# PDF Service

Start the service with its tested runtime profile:

```powershell
$env:PDF_SERVICE_TOKEN = "a-long-random-shared-token"
docker compose up -d --build
```

The Spring backend must use the same `PDF_SERVICE_TOKEN`. A backend in the
same Docker network uses `http://replysis-pdf-service:3001`; a backend on the
same host can use `http://127.0.0.1:3001`.

The service runs as a dedicated non-root user and retains Chromium's sandbox.
Do not add `--no-sandbox` or a read-only root filesystem: Chromium cannot
render safely with either configuration in the supported Docker runtime.
