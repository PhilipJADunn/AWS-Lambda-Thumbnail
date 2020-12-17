# AWS-Lambda-Thumbnail
Resize an image uploaded to an S3 bucket and store thumbnail in another S3 bucket.

First we want to create our source and destination buckets:

![Source bucket](https://user-images.githubusercontent.com/68379635/102211787-0b5fa480-3ecc-11eb-9e7d-b41679e60e88.PNG)

![Dest bucket](https://user-images.githubusercontent.com/68379635/102212624-6d6cd980-3ecd-11eb-9c48-895e3de20162.PNG)

Note here we have added "-resized" at the end.

Next we want to create an Lambda function from scratch, "thumbnail-image" and we create a new execution role as per best practice.
Once this has been created we want to add an event trigger, and this is the source bucket we created earlier and Event type is 'All object create events'.
You will also want to change the Handler to CreateThumbnail.handler:

![Trigger](https://user-images.githubusercontent.com/68379635/102214532-54195c80-3ed0-11eb-9f60-8b263fe76e39.PNG)

Now we want to upload our zip folder to the Lambda function from another S3 bucket where we store our code:

![Zip](https://user-images.githubusercontent.com/68379635/102215430-9db67700-3ed1-11eb-8842-d8df4eee7fca.PNG)

Once we have uploaded the zip file we can add an image to our source bucket:

![Upload Image](https://user-images.githubusercontent.com/68379635/102215853-33ea9d00-3ed2-11eb-89e7-947b85231e98.PNG)

When this is uploaded this will run the Lambda function that will turn the image into a thumbnail and store it in our other bucket ending "-resized":

![Thumbnail](https://user-images.githubusercontent.com/68379635/102216251-c3904b80-3ed2-11eb-9d2a-7e3350b1ccea.PNG)

Note the size difference of the images. That's how to resize an image using S3 and Lambda.
