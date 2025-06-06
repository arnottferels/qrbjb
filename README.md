# qrbjb

## Run local

1. Install `mkcert` and `http-server` (skip if installed):

   ```sh
   choco install mkcert
   npm i http-server -g
   ```

2. Then run this to create certs and start the server:

   ```powershell
   # get ip
   $ip = (Get-NetIPAddress -AddressFamily IPv4 | Where { $_.IPAddress -notlike "127.*" } | Select -First 1).IPAddress

   # make cert folder
   New-Item -ItemType Directory -Force -Path "cert" | Out-Null

   # create cert
   mkcert -cert-file "cert/$ip.pem" -key-file "cert/$ip-key.pem" $ip

   # run https
   http-server -S -C "cert/$ip.pem" -K "cert/$ip-key.pem" -p 443
   ```

## Files

```txt
/
├── index.html           Current version (uses html5-qrcode)
├── v0/
│   └── index.html       Original version (zxing, not updated)
└── v0-updated/
    └── index.html       v0 updated with html5-qrcode (compatible with current libs)

```

## Credits

Sound effect from [Pixabay](https://pixabay.com/sound-effects/store-scanner-beep-90395/)
