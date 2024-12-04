# Visualisation proposals

In this section are the different visualisation whom you can use in markdownfiles.

## 1. first titles

H1 title (biggest)(visualization proposals)
## H2 title
### H3 title
#### H4 title
##### H5 title
###### H6 title
**This is bold text without being a heading.**


## 2. Info boxes

**MARKDOWN**

!!! info "Info Box Title"
    This is an example of an info box. Use this for important or additional notes.

!!! info "This is a blue info box styled for emphasis."

> ℹ️ **This is a self made info box through markdown**

**HTML**

<div style="border: 1px solid #2196F3; background-color: #E3F2FD; padding: 10px; border-radius: 5px;">
  <strong>ℹ️ Info:</strong> This is a manually styled info box in HTML.
</div>


## 3. warning boxes

**MARKDOWN**

!!! warning "Warning Box Title"
    This is an example of a warning box. Use this to highlight critical information.

!!! warning "This is a warning box to alert users of potential issues."

> ⚠️ **This is a self made warning box through markdown**

**HTML**

<div style="border: 1px solid red; background-color: #ffebee; padding: 10px; border-radius: 5px;">
  <strong>⚠️ Warning:</strong> Ensure you save your work before continuing.
</div>


## 4. images with captions

**HTML**

<figure>
  <img src="/Markdownfiles/visualization_proposals/images/download.png" alt="Description of the image" style="max-width: 100%; text-align: center;">
  <figcaption>Figure 1: This is a caption in HTMl through markdown.</figcaption>
</figure>

**MARKDOWN**

![Description of the image](images/download.png)
*Figure 1: This is a caption in markdown.*

| ![test](images/download.png) |
|:------------------------------------------------------------------:|
| *This is a caption in markdown*|

## 5. Aligning Images (left or centered)

**HTML**

<div style="text-align: center;">
  <img src="/Markdownfiles/visualization_proposals/images/download.png" alt="Description" style="max-width: 100%;">
</div>

<div style="text-align: left;">
  <img src="/Markdownfiles/visualization_proposals/images/download.png" alt="Description" style="max-width: 100%;">
</div>

**MARKDOWN**

![test](images/download.png)

!!! info "Image Example"
    <div style="text-align: center;">
        <img src="/Markdownfiles/visualization_proposals/images/download.png" alt="Image Description" style="max-width: 100%;">
    </div>


## 6. adding links

**MARKDOWN**

[Click here to view the documentation, Made in MD](https://example.com)

!!! info "🔗 External Link"
    [Visit the official site, made in MD](https://example.com) for more information.

!!! info "🔗 Link to GISwater"

[Link to GISWATER](https://github.com/Giswater/giswater_dbmodel/wiki){ .md-button .md-button--primary }

[Link to GITHUB](https://github.com/Giswater/giswater_dbmodel/wiki){ .md-button .md-button--secondary }

**HTML**

<div style="border: 1px solid #2196F3; padding: 10px; border-radius: 5px;">
  <a href="https://example.com" style="text-decoration: none; color: #2196F3;">Visit the official site, made HTML</a>
</div>

## 7. Coloring specific words

**HTML**

<span style="color: red;">This text is red.</span>

<span style="background-color: yellow; color: black;">This text has a yellow background.</span>

==Highlighted text==

!!! success "Highlighted Text"
    Use this section to emphasize important content.

## 8. tables

**MARKDOWN**

| Image                         | Caption               |
|-------------------------------|-----------------------|
| ![Image](path/to/image.png)   | *Figure 1: Caption*  |
| ![Image](path/to/another.png) | *Figure 2: Caption*  |


**HTML**
<table>
  <tr>
    <td><img src="/Markdownfiles/visualization_proposals/images/download.png" alt="Image 1" style="max-width: 100%;"></td>
    <td>Figure 1: Caption</td>
  </tr>
  <tr>
    <td><img src="/Markdownfiles/visualization_proposals/images/download.png" alt="Image 2" style="max-width: 100%;"></td>
    <td>Figure 2: Caption</td>
  </tr>
</table>


## 9. extra

!!! info "Combined Example"
    ### Centered Image with Caption
    <div style="text-align: center;">
      <img src="/Markdownfiles/visualization_proposals/images/download.png" alt="Example Image" style="max-width: 100%;">
    </div>
    *Figure 1: This is a caption.*

    ### External Link
    [Visit the Documentation](https://example.com)

    ### Warning
    !!! warning "Important Notice"
        Ensure all prerequisites are met before proceeding.

📌 **Important Note:** This is a pinned item.

``` SQL
SELECT name, age
FROM users
WHERE age > 18
ORDER BY name ASC;
```

```python
def add(a, b):
    return a + b
print(add(2, 3))
```