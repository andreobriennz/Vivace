# Vivace 
A collection of dynamic web tools designed to increase performance through dynamic rendering on small websites

The repo contains two main files in the assets/javascript directory: vivace.js (the Vivace JavaScript library) and v-template.js (the optional Vivace templating engine)

## Vivace Library v0.3.0 (beta)
Add the vivace.js file to your project, the same way you would jQuery or any other file. You can not use the following functions

ToggleClass(Id, Class); 
Pass in the ID of an element and the class which should be toggled on and off.

HideOrShow(Id, Display, Variable);
Pass in the ID of the element, the CSS display property (eg 'none' or 'block'). 
Variable is an optional parameter (but recommended if this function is used multiple times). If you pass in a variable the library will use that in place of an ID. 

FadeIn(Id);
FadeOut(Id);
This required a small amount of CSS to be copied to your project. See the website for an explanation: https://variojs.andreobriennz.com

ScrollTo(To, Duration);
Pass in distance to scroll, and over how long.

UpdateContent(Id, Content, Variable);
Pass in the ID of the element and the content to be added to it. Similar to HideOrShow() you can optionally pass in a variable for a slight performance benefit when updating content multiple time.

function ClearInput(Id);
Enter the Id of an input to clear its value.

ReturnAttrbute(Id, AttributeType); 
Pass in the ID of an element and the attribute type you want to get and it will return it's value.

GetAttribute(Id, AttributeType, Variable);
Same as above except the value will be saved as a variable name you pass in. The variable will be global, so the ReturnAttribute() function is typically preferable.

UpdateAttribute(Content, Id, AttributeType);
Pass in content, an ID and the attribute type you want to updated. For example, UpdateAttribute("pink", "div1", "class") would set the class attribute on a #div1 to be "pink"

CreateNode(ParentId, NewTagType, Text, AttributeType, AttributeName);
Not often used, but occasionally useful. This allows new nodes to be created in the DOM (for example when making a list). The last two parameters are optional.

VirtualNodeTree(ParentId, TagType, Array, AttributeType, AttributeName);
This also creates a list, but will create the list as a whole, rather than one thing at a time. This simple 'virtual DOM' increases performance over standard JavaScript when rendering arrays. It is used by the Vivace templating engine.

LazyLoad(src);
This useful function creates a script tag where the 'src' parameter is the link to the JavaScript file.

AjaxGet(Name, Url);
This function is a way to use AJAX and JSON without jQuery. It is currently in beta.


For a visual demonstration, many of these functions on on the website: https://vivace.andreobriennz.com


## Vivace Templater v0.0.2 (alpha)

To use the templater,

1. Add the v-templater.js, as well as vivace.js if it is not already added (both files are located in assets/javascript). Then create new JavaScript file, and link to it as well

2. Set a variable called "pages" to be a JSON object where each key (eg "" for the home page) matches the URL of an anchor tag after the last slash, and the value is the of the page (eg "home")

3. Create a model file which matches the above name, but with a .js extension (eg "home.js") in the assets/models directory

4. Inside the file, create a JSON object for that page where the key is an identifier and the value is content to put output to the DOM. The JSON should not be made into a variable. (eg { "title" : "Welcome" })

5. In the HTML, add a v="" attribute with property name of one of the keys from step 4 (eg &lt;title v="title"&gt;Home&lt;/title&gt;

6. Call Render() and the page should update with content
