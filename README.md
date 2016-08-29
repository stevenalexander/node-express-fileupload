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

## Run in Docker container

The upload path can be set via environmental variable and used in a container

To build:

```
docker build -t "node_fileupload:dockerfile" .
```

To run:

```
docker run -p 3000:3000 -e "UPLOADS=/uploads" --volume=/MYPATH/uploads:/uploads node_fileupload:dockerfile
```