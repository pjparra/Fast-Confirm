Fast Confirm was born when I felt the need to ask confirmation to users on some actions performed on widgets. The small-sized nature of these widgets, and their ease of use pushed me to design a clean, non intrusive way of asking confirmations. A traditional dialog box, with jQueryUI for example would have disturbed the workflow a bit too much. I also needed something that clearly indicated from where the message came from.

So I decided to do my own plugin for this. It had to be lightweight, easy, clean looking, flexible but not with tons of options. So there is no auto-positioning stuff: if you decide to position it on top of your trigger element, it will be on top, even if it is off-page. It's your business to decide which side of your trigger element is suitable to receive the confirm box.

This plugin doesn't use any image, which makes it extra lightweight. Thanks to Addy Osmani for his excellent video about CSS3, by the way. :-)

Since version 2.0, you can let Fast Confirm take care of the events management, which permits to use it really simply with form submissions for instance.

Basic usage:
JS

The jQuery object to which you apply the plugin will be the trigger of the confirmation box. This trigger will be passed along in the parameters for the callback functions.
View Raw Code?

    $('#try').fastConfirm(options);

What else?
You can also call methods, the jQueryUI way:
View Raw Code?

    $('#try').fastConfirm('close');

HTML

Just any valid HTML element:
View Raw Code?

    <button id="try">Try it!</button>

CSS

A CSS file is included in the downloadable package. But you might want to add some custom CSS to make the integration more seamless.

You'll see in the included CSS file that there are two sections, the first one shouldn't be edited, it is a part of the plugin behaviour, and the second part contains what is relative to the look & feel, so you can customize it (if you want a red background for your confirmation box for example).