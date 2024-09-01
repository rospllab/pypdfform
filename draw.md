# Draw stuffs

PyPDFForm allows you to draw certain elements on a PDF. The purpose is in case there is a missing widget on your PDF 
form, and you need to put certain texts on it, or if you need to draw images.

This section of the documentation will use 
[this PDF](https://github.com/chinapandaman/PyPDFForm/raw/master/pdf_samples/sample_template.pdf) as an example.

This section of the documentation requires a basic understanding of [the PDF coordinate system](coordinate.md).

All optional parameters will have a comment `# optional` after each of them.

**NOTE:** Due to a known bug in a dependency, it is advised that these draw methods are called after 
a PDF form is filled. Otherwise, part (most noticeably radio buttons) or even all widgets of the PDF form might 
get removed after drawing things on it.

## Draw text

```python
from PyPDFForm import PdfWrapper

pdf = PdfWrapper("sample_template.pdf").draw_text(
    text="random text",
    page_number=1,
    x=300,
    y=225,
    font="your_registered_font",    # optional
    font_size=12,   # optional
    font_color=(1, 0, 0)    # optional
)

with open("output.pdf", "wb+") as output:
    output.write(pdf.read())
```

## Draw image

```python
from PyPDFForm import PdfWrapper

pdf = PdfWrapper("sample_template.pdf").draw_image(
    image="sample_image.jpg",
    page_number=1,
    x=100,
    y=100,
    width=400,
    height=225,
    rotation=0  # optional
)

with open("output.pdf", "wb+") as output:
    output.write(pdf.read())
```
