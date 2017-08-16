`file — determine file type`

```
shell> file --mime-type example_image.png
example_image.png: image/png
shell> file --mime-type example_image.png | sed 's/.*: //'
```

