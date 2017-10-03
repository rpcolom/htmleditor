# CRM 2013-D365 Basic HTML Editor / Rich Text
[![download](https://user-images.githubusercontent.com/14048382/27844360-c7ea9670-6174-11e7-8658-80d356c1ba8f.png)](https://github.com/PaulNieuwelaar/htmleditor/releases/download/v1.1/HTMLEditor_1_1_0_0.zip) [<img align="right" src="https://user-images.githubusercontent.com/14048382/29433676-4eb13ea6-83f4-11e7-8c07-eca514b1b197.png"/>](https://github.com/PaulNieuwelaar/htmleditor/wiki/Documentation)

![](https://user-images.githubusercontent.com/14048382/29442838-47f93e36-8428-11e7-8496-e46ea8c678ff.png)

## Overview
CRM by default doesn’t allow us to create our own custom fields using rich text or HTML, similar to the email Description out of the box. However, if we’re building forms that push data to a website dynamically, we may need the ability to build some HTML in CRM. In the past there’s been a few solutions available to do this in CRM. Some are more unsupported than others (e.g. hacking into a field on the form and converting it into a rich text editor).

One of the nicer solutions involves embedded a web resource on the form, and then taking the HTML generated by the web resource, and updating a field on the parent form. A good example of this, and the baseline of my solution is shown here, by Thomas Unzeitig: http://soho.at/wp/create-rich-text-textarea-microsoft-crm-2013-forms.

This solution is using [CKEditor](http://ckeditor.com/), which is a tidy HTML/JavaScript based html editor, which means we can upload all of the web resources into a CRM solution and keep everything packaged nicely.

## How it Works
Check out the [Documentation](https://github.com/PaulNieuwelaar/htmleditor/wiki/Documentation) page for installation and usage details.

I have made the solution dynamic enough so that it can be dropped into any form by simply embedding the html editor web resource into the form, and passing in the field name to store the HTML data.

![](https://user-images.githubusercontent.com/14048382/29442839-48027eb0-8428-11e7-9516-224762df4d24.png)

You can also set the Formatting to display the number of rows required, and to disable the iframe scrolling and border for a nicer look and feel. The HTML Editor will automatically expand to fill the space available inside the iframe, however big you choose to make it.

![html3](https://user-images.githubusercontent.com/14048382/29442837-47e0bb72-8428-11e7-8d5b-9ee150bf0ce2.png)

You can also pass a default value into the HTML editor, which will be applied when there is no existing value (e.g. for new records). This can be useful when you want to ‘guide’ users into entering the HTML in a specific format, rather than just letting them loose.

The default value needs to be encoded, and then included in the custom parameters of the web resource. You can get the encoded URL string from the following webpage by pasting in some HTML and then clicking ‘Encode’: http://meyerweb.com/eric/tools/dencoder. Copy the encoded string and add it to the web resource parameters after the field value, e.g. field=new_html&defaultValue=%3Cb%3EHello%3C%2Fb%3E

![html4](https://user-images.githubusercontent.com/14048382/29442836-47b886ca-8428-11e7-8a31-dfa62162db1e.png)

The defaultValue parameter is optional, and if not specified, the HTML editor will simply display nothing initially.

Next we can preview our form and see that the html editor just works. We can see the default value being applied, including the ‘bold’ styling, and our basic editing tools are available.

![html5](https://user-images.githubusercontent.com/14048382/29442841-480b5e86-8428-11e7-8613-742dde0af59f.png)

The data from the HTML editor will be saved to the ‘HTML’ field every time you click out of the iframe. This means you don’t need to manually ‘save’ the HTML, it will just automatically keep up to date by itself. After we’ve saved the form, we can reload the page and the HTML editor will load up the HTML from our field automatically. 

![html6](https://user-images.githubusercontent.com/14048382/29442840-47ffda66-8428-11e7-8872-5a4dbb3ebb6b.png)

We can now hide that HTML field (as long as it remains on the form), and the HTML editor will continue to work and look pretty.

The buttons/editing tools available in this solution are based on the ‘Basic’ package provided by CKEditor. This is because the basic package seemed to meet our particular needs as we didn’t require a full blown HTML editor, just some basic rich text editing tools. This also means the entire solution is only 17 web resources.

If however you do require any additional editing tools, you can check out the [CKEditor download page](http://ckeditor.com/download) and create yourself a custom download package, and then just be sure to upload the missing web resources using the same publisher prefix, and same file names, then update the config.js file to load those plugins as well.

Note that this solution works in CRM 2013, and up to Dynamics 365, and works on any entities. You can also add the HTML editor to the same form multiple times, each referencing different fields.

Created by [Paul Nieuwelaar](http://paulnieuwelaar.wordpress.com) - [@paulnz1](https://twitter.com/paulnz1)  
Sponsored by [Magnetism Solutions - Dynamics CRM Specialists](http://www.magnetismsolutions.com)

[![](https://user-images.githubusercontent.com/14048382/30045114-3805d840-9256-11e7-9bdb-323760fb43ea.png)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=PYR3TWPGRSDVW)
