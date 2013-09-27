
I have to projects, Masonry and Isotope. You might have seen them. Masony is a layout library that does this. And Isotope is the layout library that does Masonry and does filtering and sorting, so you can do this.

     _____    _____
    |     |  |     |
    |  M  |  |  I  |
    |_____|  |_____|

But there's a problem of using layouts. Basically you need all images to be loaded before you trigger the layout.


## imagesLoaded

Brought in the JS, imagesLoaded. Some JS that triggers a callback when all images have been loaded

Put it into Masonry and into Isotope, as well as its own repo

     _____    _____    __
    |     |  |     |  |iL|
    | M __|  |  I__|  |__|
    |__|iL|  |__|iL|


