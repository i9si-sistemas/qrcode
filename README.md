# QR Code Encoder

<img src="gopher.png" width="200" />

Modern and optimized rewrite of [go-qrcode](https://github.com/skip2/go-qrcode)

## Requirements

- Golang 1.24.1 or higher
  - [Download](https://go.dev/dl/)

## Usage

```go
package main

import (
	"image/color"
	"log"

	"github.com/i9si-sistemas/qrcode"
)

func main() {
	qr, err := qrcode.New(
		"https://www.i9sisistemas.com.br/",
		qrcode.Highest,
	)
	if err != nil {
		log.Fatalf("Failed to create QR Code: %v", err)
	}

	if err := qr.WithNoBorder().WithColors(
		color.RGBA{0x00, 0x00, 0x00, 0xff},
		color.RGBA{0xef, 0xef, 0xef, 0xff},
	).WriteFileWithoutSize("qrcode_example.png"); err != nil {
		log.Fatalf("Failed to save QR Code: %v", err)
	}
}
```
