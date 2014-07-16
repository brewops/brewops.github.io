# BrewOps Site

This is a Jekyll-based site. Instructions for posting are below.

### Adding Posts and Pages

There are two main content layouts: `post.html` (for posts) and `page.html` (for pages). Both have support for large **feature images** that span the full-width of the screen, and both are meant for text heavy blog posts (or articles).

There are two rake tasks that can be used to create a new post or page with all YAML Front Matter. Using either `rake new_post` or `rake new_page` will prompt you for a title and tags to classify them. Example below:

```bash
rake new_post

Enter a title for your post: My Awesome Post
Enter tags to classify your post (comma separated): web development, code
Creating new post: _posts/2014-02-10-my-awesome-post.md
```

By default posts and pages will be created in MarkDown using the `.md` extension.

#### Feature Images

A good rule of thumb is to keep feature images nice and wide so you don't push the body text too far down. An image cropped to around 1024 x 256 pixels will keep file size down with an acceptable resolution for most devices.

The two layouts make the assumption that the feature images live in the *images* folder. To add a feature image to a post or page just include the filename in the front matter like so. 

```
image:
  feature: feature-image-filename.jpg
  thumb: thumbnail-image.jpg #keep it square 200x200 px is good
```

If you want to apply attribution to a feature image use the following YAML front matter on posts or pages. Image credits appear directly below the feature image with a link back to the original source.

```
image:
  feature: feature-image-filename.jpg
  credit: Michael Rose #name of the person or site you want to credit
  creditlink: http://mademistakes.com #url to their site or licensing
```

#### Post/Page Thumbnails for OG and Twitter Cards

Post and page thumbnails work the same way. These are used by [Open Graph](https://developers.facebook.com/docs/opengraph/) and [Twitter Cards](https://dev.twitter.com/docs/cards) meta tags found in `head.html`. If you don't assign a thumbnail the image you assigned to `site.owner.avatar` in `_config.yml will be used.

#### Videos

Video embeds are responsive and scale with the width of the main content block with the help of [FitVids](http://fitvidsjs.com/).

Not sure if this only effects Kramdown or if it's an issue with Markdown in general. But adding YouTube video embeds causes errors when building your Jekyll site. To fix add a space between the `<iframe>` tags and remove `allowfullscreen`. Example below:

```
<iframe width="560" height="315" src="http://www.youtube.com/embed/PWf4WUoMXwg" frameborder="0"> </iframe>
```

#### Social Share Links

To enable Facebook, Twitter, and Google+ share links on a post or page, add the following to its front matter:

```
share: true
```

#### Twitter Cards

Twitter cards make it possible to attach images and post summaries to Tweets that link to your content. Summary Card meta tags have been added to `head.html` to support this, you just need to [validate and apply your domain](https://dev.twitter.com/docs/cards) to turn it on.

#### Link Post Type

This site supports **link posts**, made famous by John Gruber. To activate just add `link: http://url-you-want-linked` to the post's YAML front matter and you're done.