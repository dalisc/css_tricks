## 5 Little CSS Tricks to Make Your Website Go a Long Way

Your website doesn’t have to look boring and it really doesn’t take complicated CSS to revolutionise your website. I’m about to show you nine simple (I really mean it!) CSS tricks to elevate your webpage. Little changes here and there significantly spruce up the look.

Here is a simple website. It’s perfectly fine - simple, informative, and readable. It’s even got some nice pictures in it.




Now, we want to transform this website! And with several easy tricks, we can introduce some wow factors into it. Here is our goal:




Looks pretty cool now, doesn’t it? It doesn’t take a lot of changes to arrive at this. I’ll take you through them. Let’s start from the simplest ones.

Text select colour



This is something that can be changed in very few lines of code but is often overlooked! The tiniest details count and if you change the default select/highlight colors to colors that suit the theme that you’re going for, your visitors will pick up on it and have a better experience browsing your site.

To change the select/highlight colour and text color, simply specify them like so:

    ::selection {
        background-color: #013896;
        color: #f1f1f1;
    }


Drop caps


To get that professional article/newspaper look, you can use a drop cap for the first letter of your text. The drop cap is that large capital letter, which you can stylize in any way you like to suit the theme of your webpage. There are several ways to implement the drop cap in CSS. What I’m doing is really simple.
I put the first letter in a span tag like so: 
<span class="dropcap">T</span>he places I dream of

Then with CSS, I decorate the drop cap class. 

    .dropcap {
        float: left;
        font-size: 400%;
        color: #cf142b;
        margin: -13px 7px -13px 0;
    }

Mainly I need to make sure that I set it as a floating object. The size and color is completely up to you. Afterwards, adjust the margins to make it look perfect. 

One letter really makes a difference!
Image overlay

	
An image overlay is a visual treat when the mouse hovers over an image. It can
serve many purposes from just decoration to revealing a hidden element such as a button. There are many styles that you can find on the internet. In my article, I’ve chosen to replace the url link to the original article with an image of the logo of the original publisher. When the mouse hovers over that image, a simple text fades in. 

                <div class="container">
                    <a href="https://luxurylondon.co.uk/travel/international/cambodia-luxury-hotels-review/"><img src="https://luxurylondon.co.uk/images/frontend/logos/luxury-london-logo.png" alt="Avatar" class="image"></a>
                    <div class="overlay">
                        <div class="text">Go to site.</div>
                    </div>
                </div>


The idea is to place the image and overlay (whatever it may be) on top of each other. Make the overlay invisible unless the mouse hovers over it. This can be changed in the opacity attribute. To make things smooth, specify a time for the transition as well. Take note of the transition and opacity in the code below:

    .overlay {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        height: 100%;
        opacity: 0;
        transition: 0.5s ease;
        background-color: #cf142b;
    }

    .container:hover .overlay {
        opacity: 0.8;
        cursor: pointer;
    }

Colorize and zoom into image on hover

This is one of my favorite tricks. It changes an image from being boring and static to something interactive. Firstly you’d need to wrap your image in a container. Let’s give the container the class name “image image-colorize”.

You must set the overflow attribute of the container to hidden for the effect to work.

The trick is actually an image overlay trick. Set the image to be in grayscale by default, then take away that filter when the mouse hovers over the image. Zoom can be adjusted with transform: scale(your_ratio);.

    .image {
        width: 100%;
        overflow: hidden;
    }
    .image-colorize img {
        transition: transform .5s, filter 0.5s ease-in-out;
        filter: grayscale(100%);
    }

    .image-colorize:hover img {
        filter: grayscale(0);
        transform: scale(1.1);
    }


There is an excellent blog post on various other styles that you can implement.
Play with image masking
Now we’re entering the realm of the pros, but you don’t need pro skills to make this effect happen. Image masking is a method of cropping out an image in a specific form. That form is determined by a second image, where that image solely contains the shape of the mask and everything else is transparent. It’s easier to understand with visuals.

If this is my image: 

And this is my mask (the white part is actually transparent):

Then this will be the result of masking the image:


The advantage of masking the image is that the image isn’t exactly a rectangular box as usual so you can do some interesting things as you can see from the gif. (Imagine a sun setting/rising behind Angkor Wat!). Of course, no one’s going to know your image is masked unless you play with those sorts of effect!

As you can see, what I’ve done is hide the “Cambodia” text behind Angkor Wat as you scroll down. In the original version, if you scroll down, “Cambodia” would just disappear above. So we need to prevent that. What we can do is to sticky the text so that it always stays in view until it disappears behind our image.

Here is the styling for the text:

    div.sticky {
        position: -webkit-sticky;
        position: sticky;
        top: 0;
        z-index: -999;
        padding: 50px;
        text-align: center;
        font-size: 150px;
        margin-bottom: -70px;
    }

“position: sticky” is what makes that element sticky. Another important one is the z-index. Something with a z-index higher than another thing will be seen on top. We want the text to disappear behind the image, so we set it’s z-index to be less. (Doesn’t have to be all the way to -999).

One last step. Wrap the image and text in a header tag, or else “Cambodia” would be seen behind the main article as well.

<header>
// all those mask tricks
</header>

// rest of document



Wrapping up (pun intended)

All these beautiful tricks are more than just nice-to-have’s. If you’re a web developer that’s just starting out, playing with CSS is a great way to learn about the possibilities and limitations of CSS, and enjoy the designing process along the way. If you want to build a website for your business, these little details go a long way in elevating the customer experience and enticing them to stay on your website longer. What we worked with today is pure CSS, and you can revamp sites pretty well already with that. Incorporating Javascript will bring it to a whole new level. There are plenty of resources for learning online, and once you’ve mastered the basics, don’t be afraid to dive into styles that require more technical know-how. 

Get the source code of the before and after websites at this repository:https://github.com/dalisc/css_tricks

