# Assignment 4: Images & Media - Visual Content

**By Mahendra Bagul**

A website without images is like a book without pictures - technically complete but not engaging! Let's add visual and multimedia content.

---

## 📚 What You'll Learn

- ✅ `<img>` tag and attributes (src, alt, width, height)
- ✅ Image formats (JPG, PNG, SVG, WebP)
- ✅ Figure and figcaption
- ✅ `<audio>` and controls
- ✅ `<video>` element
- ✅ `<iframe>` for embedded content
- ✅ Responsive images
- ✅ Image accessibility

---

## 🎯 Assignment Objectives

Create a "Photo Gallery & Media Showcase" website with images, audio player, and video.

**Difficulty**: ⭐⭐⭐☆☆  
**Time**: 3-4 hours  
**Prerequisites**: Assignments 1-3

---

## 📋 Requirements

### Must Have
1. ✅ At least 6 images with proper alt text
2. ✅ At least 2 figures with captions
3. ✅ At least 1 audio player with controls
4. ✅ At least 1 video player with controls
5. ✅ At least 1 embedded YouTube video (iframe)
6. ✅ Proper image sizing
7. ✅ All images have alt attributes
8. ✅ Organized gallery layout

---

## 💻 Key HTML Elements

### Images
```html
<!-- Basic image -->
<img src="photo.jpg" alt="Description of photo">

<!-- With dimensions -->
<img src="photo.jpg" alt="Description" width="600" height="400">

<!-- With figure -->
<figure>
    <img src="photo.jpg" alt="Description">
    <figcaption>Photo caption here</figcaption>
</figure>
```

### Audio
```html
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    <source src="audio.ogg" type="audio/ogg">
    Your browser doesn't support audio.
</audio>
```

### Video
```html
<video controls width="640" height="360">
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    Your browser doesn't support video.
</video>
```

### Embedded Content
```html
<!-- YouTube video -->
<iframe width="560" height="315" 
    src="https://www.youtube.com/embed/VIDEO_ID" 
    frameborder="0" allow="accelerometer; autoplay; encrypted-media" 
    allowfullscreen>
</iframe>
```

---

## 🏗️ Implementation Structure

```html
<h1>My Photo Gallery</h1>

<!-- Gallery Section -->
<section>
    <h2>Nature Photos</h2>
    <figure>
        <img src="mountain.jpg" alt="Snow-capped mountain at sunset" width="400">
        <figcaption>Mountain Peak - Captured in Nepal, 2024</figcaption>
    </figure>
    <!-- More images... -->
</section>

<!-- Audio Section -->
<section>
    <h2>My Podcast</h2>
    <audio controls>
        <source src="episode1.mp3" type="audio/mpeg">
    </audio>
</section>

<!-- Video Section -->
<section>
    <h2>Video Tutorial</h2>
    <video controls width="640">
        <source src="tutorial.mp4" type="video/mp4">
    </video>
</section>
```

---

## ✅ Self-Assessment

- [ ] 6+ images with descriptive alt text
- [ ] At least 2 figures with captions
- [ ] Audio player works with controls
- [ ] Video player works with controls
- [ ] YouTube video embedded correctly
- [ ] All media loads properly
- [ ] Images are appropriately sized
- [ ] Accessibility: alt text is meaningful

---

## 💡 Image Best Practices

1. **Always include alt text** - Essential for accessibility
2. **Optimize file size** - Compress images before uploading
3. **Use correct format**:
   - JPG: Photos
   - PNG: Graphics, transparency
   - SVG: Icons, logos
4. **Specify dimensions** - Prevents layout shift

---

**Next**: [Assignment 5: Tables & Data](../assignment-05-tables-data/ASSIGNMENT_5_GUIDE.md)

---

**Created by**: [Mahendra Bagul](https://github.com/bagulm123)

