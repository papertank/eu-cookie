# Papertank Cookie v0.2

A simple jQuery plugin for compliance with the new EU cookie legislation. Decided to design / code up a toggle 'On / Off' tooltip box, encouraging the user to accept cookies (rather than the boring 'I Accept Cookies' button).

## Installation

Include the cookie.js script *after* the jQuery library (unless you are packaging scripts somehow else):

    <script src="/path/to/cookie.min.js"></script>

## Usage

Once you have referenced the cookie plugin above, you can call it using jQuery. You should do this *before* you call your cookie dependant javascript. *Update: Do not wrap the jquery plugin call in document ready wrapper.*

  	$.pt_cookie();
  	
If you have javascript plugins that require cookies to operate - eg. analytics or facebook, etc - you should wrap them as follows (remember to use jQuery document ready to make sure cookie plugin is loaded): *Updated: Do not wrap analytics call code in jquery document ready wrapper.*
	
	if ($.cookie_accepted()) {
	
		`analytics, etc code here…`
		
	}

If you have parts of your website's markup that require cookies to operate, give them the class `requires_cookies`. E.g Facebook buttons, etc.

	<div class="social requires_cookies">
            		
       <div class="fb-like" data-href="http://example.com" data-send="false" data-layout="button_count" data-width="90" data-show-faces="false" data-font="lucida grande"></div>
        
    </div>

The plugin will automatically give elements with that class the content:

	Sorry, you need to <a href="#" class="pt-euc_enable_cookies">Enable Cookies</a> for this part of the website. <small>&nbsp; <a href="/cookies" target="_blank">Learn More</a></small>
	
Additionally, any clickable elements which you give the class `pt-euc_enable_cookies` to will enable cookies when clicked.

## Options

Options are passed to the plugin call as follows (defaults below).

  	$.pt_cookie({
		info_link: "http://www.allaboutcookies.org/",
        message: "We need your consent to store cookies on your computer. These improve your experience and help us remember you.",
        info_label: "Learn More",
        close_label: "Close",
        css_path: '/',
        cookie_domain: '',
        cookie_expires: 365,
        default_action: 'accept',
        always_show: false,
        expires: 365
  	});

Specifics…

	css_path: '/'
	
The plugin will look for the cookie.css file in the path given here. Eg. you could use Wordpress theme path. (Remember the images remain in the same folder the default css).

	cookie_domain: ''
	
Used for websites with subdomains, so that cookie can be remembered across websites. 

	default_action: 'accept'
	
Defines what the default action should be - automatically deny cookies, or automatically accept them (the first time a user visits the website).

	always_show: false,

If true, the cookie tooltip window will always show (from the first time the user visits), until they choose to either accept or reject cookies.

## Development

- Source hosted at [GitHub](https://github.com/papertank/eu-cookie)

## Changelog

v0.2 (29/05/2012) - Updated js plugin with document ready wrapper around dom manipulation code. Updated readme to suggest that plugin instantiation call and IF statement (before analytics, etc code) is not wrapped in jquery document ready wrapper (was messing up Google Analytics in particular!).

## Authors

[Papertank](https://github.com/papertank)

## Credits

Cookie Icon - http://www.iconfinder.com/icondetails/45928/16/bite_cookie_icon

Toggle Graphic - http://www.premiumpixels.com/freebies/onoff-switches-and-toggles-psd/

