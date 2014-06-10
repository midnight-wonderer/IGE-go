###IGE-go
My favorite cryptography mode of operation scheme for the block cipher, Infinite Garble Extension.
Since you are here I guess you know why and when to use IGE mode.

###Install
go get github.com/MidnightWonderer/IGE-go/ige

###Example Usage
`package main

import (
	"crypto/aes"
	"encoding/hex"
	"fmt"
	"github.com/MidnightWonderer/IGE-go/ige"
)

func main() {
	aesKey, _ := hex.DecodeString("5468697320697320616E20696D706C65")
	aesBlock, _ := aes.NewCipher(aesKey)
	igeIV, _ := hex.DecodeString("6D656E746174696F6E206F6620494745206D6F646520666F72204F70656E5353")
	igeEnc := ige.NewIGEEncrypter(aesBlock, igeIV)
	crypttext, _ := hex.DecodeString("99706487A1CDE613BC6DE0B6F24B1C7AA448C8B9C3403E3467A8CAD89340F53B")
	fmt.Printf("%s\r\n", hex.EncodeToString(crypttext))
	igeEnc.CryptBlocks(crypttext, crypttext)
	fmt.Printf("%s\r\n", hex.EncodeToString(crypttext))
	//print:
	//99706487a1cde613bc6de0b6f24b1c7aa448c8b9c3403e3467a8cad89340f53b
	//4c2e204c6574277320686f70652042656e20676f74206974207269676874210a
	//test vector:
	//https://web.archive.org/web/20120418022623/http://www.links.org/files/openssl-ige.pdf
}`

###etc.
IGE-go was placed under The MIT-Zero License. Contribution back is encouraged.