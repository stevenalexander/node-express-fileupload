# node-express-fileupload
Simple node web app using express with a file upload control

Uses [multer](https://www.npmjs.com/package/multer) to handle file upload.

This can also be used to control where the file is stored and named:

```
var storage = multer.diskStorage({
  destination: function (req, file, cb) {
    cb(null, '/tmp/my-uploads')
  },
  filename: function (req, file, cb) {
    cb(null, file.fieldname + '-' + Date.now())
  }
})
```