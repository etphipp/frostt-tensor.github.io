# FROSTT
The Formidable Repository of Open Sparse Tensors and Tools.


## Project structure
The FROSTT website is written with [Jekyll](http://jekyllrb.com/) and has the
following project structure:
```
frostt/
├── _layouts : Page layouts, including the dataset page layout.
├── _pages   : A catch-all for pages.
├── _posts   : News items.
├── tensors  : Pages concerning the collection, but not actually datasets.
└── _tensors : Actual datasets descriptions.
```


## Building
You can build and serve FROSTT for local development:
```
$ bundle install
$ jekyll serve --watch --detach
$ jekyll build --watch
```

Then just point your browser to [localhost:4000](localhost:4000). You can edit
any files and simply refresh the page. However, if you edit `_config.yml`, you
need to kill and restart the `jekyll build` command.


## Contributing
FROSTT thrives on community contributions. Pull requests and issues are
encouraged. To make a contribution, just fork this repository, create a branch
(with a descriptive name, please!), and issue a pull request through Github.

### Submitting a tensor

1. To submit a new tensor, create a directory in `tensors/site_data/`. We
recommend beginning with the provided template. Suppose your new tensor is
named Big-Tensor:
```
$ cp -R tensors/site_data/template tensors/site_data/big-tensor
```

2. Fill in as much information as possible about your new tensor. A few tips:
  - Citation information (`cite.bib`) and tags (`tags.txt`) are optional.
    Delete them if unused.
  - Text in `description.md` will be rendered with Markdown.
  - File listings (`files.txt`) should take the form of "big-tensor/file
    Description". These will point to the correct locations in step 4.
```
$ ls -1 tensors/site_data/big-tensor
  cite.bib
  description.txt
  dims.txt
  files.txt
  nnz.txt
  tags.txt
  title.txt
```

3. Build your tensor page:
```
$ ./scripts/driver.sh tensors/site_data/big-tensor
```
If all went well, `_tensors/big-tensor.md` should now exist. Reload your local
[FROSTT](http://localhost:4000/tensors/) and Big-Tensor should now be
available.

4. Once the tensor page is ready, submit a pull request and include a public
link to the data in `files.txt`. We will copy the data to our hosting location,
update the links in `files.txt`, merge the pull request, and go live!


