# pdf-poppler-with-password

## For Electron

Convert PDF files into images using Poppler with promises. It achieves 10x faster performance compared to other PDF converters.
Poppler library attached inside statically, so it has not require installation of poppler.

**Note: Currently it supports for Windows and Mac OS only (Mac version not stable).**
**Note: Mac version need latest libcairo.2.dylib**

## Installation
```
  $ npm i pdf-poppler-with-password
```

## Usage

### Get pdf info

```javascript
const pdf = require('pdf-poppler-with-password');

let file = 'C:\\tmp\\convertme.pdf'

pdf.info(file)
    .then(pdfinfo => {
        console.log(pdfinfo);
    });
```

### Convert pdf into image

```javascript
const path = require('path');
const pdf = require('pdf-poppler');

let file = 'C:\\tmp\\convertme.pdf'

let opts = {
    format: 'jpeg',
    out_dir: path.dirname(file),
    out_prefix: path.baseName(file, path.extname(file)),
    page: null
}

pdf.convert(file, opts)
    .then(res => {
        console.log('Successfully converted');
    })
    .catch(error => {
        console.error(error);
    })
```



### with password

```javascript
const path = require('path');
const pdf = require('pdf-poppler');

let file = 'C:\\tmp\\convertme.pdf'

let opts = {
    format: 'jpeg',
    out_dir: path.dirname(file),
    out_prefix: path.baseName(file, path.extname(file)),
    page: null,// will proses all page if empty or null value
    password:'******'
}
// convert or just get pdf info
```