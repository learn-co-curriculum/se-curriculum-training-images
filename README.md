# Working with Images

## Learning Goals

- Upload an image to a S3 bucket
- Embed an image in a lesson

## Introduction

Images are an important part of our curriculum as a way to visually demonstrate
complex materials. We use AWS S3 to host all the image files that are embedded
in our various lessons.

## Uploading Images to S3

There are a number of ways to upload images to a S3 bucket. In general, our
needs are pretty simple. The curriculum team needs a way to:

- Upload an image
- Set its permissions so it's visible to anyone
- Get a URL for the uploaded images
- (sometimes) Resize an image to display in Canvas

We created the [flatiron-s3-uploader][] Ruby gem to simplify this process.

To use this tool, follow the installation steps:

- [install flatiron-s3-uploader][flatiron-s3-uploader]

You'll need a few secret environment variables set in order to use the tool. Ask
a curriculum team member for these secrets.

To upload an image using this tool, the command looks like this:

```console
$ flatiron-s3-uploader upload path/to/image.png --bucket curriculum-content --width 600 --directory course-name/lesson-name
```

Let's give it a try! We'll try embedding an image in the readme lesson you
created previously, so you can see the full process of adding an image to a
lesson in GitHub and in Canvas. Here's an image you can use:

![Example image for uploader](https://curriculum-content.s3.amazonaws.com/phase-0/acting-on-events-lab/keyboard-event.png)

`cd` to the directory where you downloaded the image, and run:

```console
$ flatiron-s3-uploader upload keyboard-event.png --bucket curriculum-content --width 800 --directory curriculum-training/your-lesson-name
```

After the upload is complete, you'll see the URL for the uploaded image returned
in the console.

## Embedding Images in Markdown

To embed the image in your lesson, you'll need to edit the README.md file and
add a link to the image using this syntax:

```md
![alt text](image-url)
```

Try this out with your image URL, then commit and push your changes. As long as
you set up the lesson with the `.canvas` file and the GitHub action, the
uploaded image should appear on the Canvas page after the action has completed
successfully.

## Working with S3 Using Cyberduck

While the CLI tool is handy for automating many of the steps needed for
uploading images, it can also be useful to get full access to 
`curriculum-content`, the S3 bucket the Curriculum Team uses, to move or delete
files or upload images manually.

For this, we use [Cyberduck][cyberduck].

After downloading Cyberduck, you can use [this guide][cyberduck s3 guide] to
create a connection to the S3 bucket.

[flatiron-s3-uploader]:
  https://github.com/learn-co-curriculum/flatiron-s3-uploader
[cyberduck]: https://cyberduck.io/
[cyberduck s3 guide]:
  https://mediatemple.net/community/products/aws/360010862892/using-cyberduck-for-amazon-s3
