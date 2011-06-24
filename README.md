#Some context

Fast Confirm was born when I felt the need to ask confirmation to users on some actions performed on widgets. The small-sized nature of these widgets, and their ease of use pushed me to design a clean, non intrusive way of asking confirmations. A traditional dialog box, with jQueryUI for example would have disturbed the workflow a bit too much. I also needed something that clearly indicated from where the message came from.

So I decided to do my own plugin for this. It had to be lightweight, easy, clean looking, flexible but not with tons of options. So there is no auto-positioning stuff: if you decide to position it on top of your trigger element, it will be on top, even if it is off-page. It's your business to decide which side of your trigger element is suitable to receive the confirm box.

This plugin doesn't use any image, which makes it extra lightweight. Thanks to Addy Osmani for his excellent video about CSS3, by the way. :-)

Since version 2.0, you can let Fast Confirm take care of the events management, which permits to use it really simply with form submissions for instance.

#Usage

##JS

The jQuery object to which you apply the plugin will be the trigger of the confirmation box. This trigger will be passed along in the parameters for the callback functions.

    $('#try').fastConfirm(options);

What else?
You can also call methods, the jQueryUI way:

    $('#try').fastConfirm('close');

##HTML

Just any valid HTML element:

    <button id="try">Try it!</button>

##CSS

A CSS file is included in the downloadable package. But you might want to add some custom CSS to make the integration more seamless.

You'll see in the included CSS file that there are two sections, the first one shouldn't be edited, it is a part of the plugin behaviour, and the second part contains what is relative to the look & feel, so you can customize it (if you want a red background for your confirmation box for example).

##Options
There are a few options to make Fast Confirm more flexible. Here they are, with their default values:

* __position__: ['top', 'right', _'bottom'_, 'left']
    * Defines where to put the confirmation box, realtively to the trigger element.
* __offset__: {top: 0, left: 0}
    * Allows precise positioning. Top and left offsets will be added to the computed default absolute position of the confirmation box. If you set the top offset to -5 for example, the confirmation box will be 5 pixels above its default position.
* __zIndex__: 10000
    * Allows you to fine tune the z-index if you're facing z-index issues causing the confirm box not to appear
* __eventToBind__: (eventName|_null_)
    * An event name ('submit', 'click'...) or null. If an event name is provided, Fast Confirm will take care of event management. This is really useful when you want to deal with form submission. The real event (form submission for instance) will only be fired when the deferred returned by the `onProceed` callback will be resolved. By default, `onProceed` returns true, which is equivalent to a resolved deferred.
* __condition__: (function|_null_)
    * A function returning a boolean, or null. If a function is provided, the confirm box will only appear if the condition function returns true. Has no effect if `eventToBind` is null.
* __questionText__: "Are you sure?"
    * The question asked by the confirm box.
* __proceedText__: "Yes"
    * The text of the button designated to confirm the action
* __cancelText__: "No"
    * The text of the button designated to cancelthe action
* __targetElement__: null
    * A selector to specify on which element, inside the binded element, the confirm box should be opened. Mostly useful to open the box on the submit button of a form.
* __unique__: [true, _false_]
    * If set to true, only one confirm box can remain opened. Any new confirm box will close opened boxes, triggering the "cancel" action on each one.
* __fastConfirmClass__: 'fast_confirm'
    * The CSS class prefix used in all Fast Confirm elements. If you want to change classes names for any reason, you have to use this parameter
* __onProceed__: function(trigger, clicked) {$.fastConfirm.close(trigger);}
    * The function called when the user hits the confirmation button. Can return a deferred object for a better event sequence control if you set the `eventToBind` parameter. You could, for instance, launch an ajax request and want to wait for it to succeed before submitting your form.
* __onCancel__: function(trigger, clicked) {$.fastConfirm.close(trigger);}
    * The function called when the user hits the cancellation button

##Methods

* __.fastConfirm('close')__: close the confirm box that is binded to the selected element.