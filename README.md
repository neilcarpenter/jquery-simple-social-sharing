# Super simple social sharings with jQueries

Just for Twitter / Facebook at the mo, opens up proper share dialog, none of that cheap `sharer.php?url=whatever` crap.

## Usage

Mark up yo links as per:

	<a data-[TYPE]="[SITE]" data-[CONTENT]="CONTENT" href="[CANONICAL SHARE URL]">Share on the [SITE]</a>

So for a real world example:

	<a data-share="facebook" data-title="Gizoogle that shiznit" data-link="http://gizoogle.net" href="https://www.facebook.com/sharer/sharer.php?u=gizoogle.net">Tell your Facebook friends! They'll love it!!</a>
	

And then the jQuery:

	$( parentContainer ).socialSharers();

It's using parent container for selector to allow event delegation, I'm presuming you would always have twitter and facebook buttons. It doesn't matter if you only have one, still just use parent container, or just `document`, whatever.

And for some customisation extras:

	$( parentContainer ).socialSharers({
		twitter: {
			handle: 'neilcarpenter' // will add 'via @neilcarpenter' on tweets
		},
		facebook: {
			appID: 144136645754967 // will load FB SDK asynchronously and add 'via [FB APP NAME]'
		}
	});

All content / events are handled through data-* attributes on the links themselves, so your options are:

- data-share => 'facebook' or 'twitter'
- data-title => Title of content to share (fb), or share text (tw). *Defaults to document `<title>`*
- data-link => Link to share. *Defaults to current `window.location.href`*
- data-image => Picture to share (fb only)
- data-description => Share text (fb only)

**Check `demo.html` for working example.**