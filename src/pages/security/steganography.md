# Steganography

Steganography is the art of hiding files inside other files.

Here is an example of how one can hide a file inside an image.

```sh
zip secret.zip my-files/
cat my-photos.jpg secret.zip > hidden.jpg
```

The hidden files can then be extracted using `unzip hidden.jpg`
