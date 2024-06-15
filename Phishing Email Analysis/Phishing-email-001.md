# Hello World, This will be one of my Email Phishing project 001

<image src="https://github.com/TommyP702/TanPham/assets/169327735/4b2a88b9-dcd7-442b-91fa-8daaf22777d4" alt="Image from GitHub" class="wp-image-5001" width="400" height="300"/>
<p><font size="+2">NOTE: even tho sometime many OSINT url scanners say clean, we cannot determine if its a false positive. credit goes to my mentor steven that reminded me to always be on my toes when it comes to phishing as threat actors will find new method to compromised someone account.</font> </p>

I'll be guiding you through the steps and processes I'll be taking. Lets have some fun!

<p class="has-text-align-center"><strong>Investigate</strong></p>

<!-- wp:group {"layout":{"type":"flex","orientation":"vertical"},"fontSize":"small"} -->
<div class="wp-block-group has-small-font-size"><!-- wp:list {"ordered":true} -->
<ol><!-- wp:list-item -->
<li><a href="#1">What is the return path of the email?</a></li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li><a href="#2">What is the domain name of the url in this mail?</a></li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li><a href="#3">Is the domain mentioned in the previous question suspicious?</a></li>
<!-- /wp:list-item -->
<!-- wp:list-item -->
<li><a href="#4">What is the body SHA-256 of the domain? </a></li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li><a href="#5">Is this email a phishing email? </a></li>
<!-- /wp:list-item -->

<!-- wp:separator -->
<hr class="wp-block-separator has-alpha-channel-opacity"/>
<!-- /wp:separator -->

<!-- wp:paragraph {"align":"center","backgroundColor":"pale-cyan-blue"} -->
<p class="has-text-align-center has-pale-cyan-blue-background-color has-background" id="1"><strong>Preparation Phase</strong></p>
<!-- /wp:paragraph -->

<p>scenario</p>
<p>Your email address has been leaked and you receive an email from Paypal in German. Try to analyze the suspicious email.</p>


<image src="https://github.com/TommyP702/TanPham/assets/169327735/cfbb152e-9a9b-4dad-a1d9-83eb16439a89" alt="Image from GitHub" class="wp-image-5001"/>

<p>Let inspect the header, I had an issue with loading microsoft outlook since the network is isolated so I had to use Firefox Thunderbird </p>

<image src="https://github.com/TommyP702/TanPham/assets/169327735/ef38d773-080a-4b09-bc9b-c00601e87fbc" alt="Image from GitHub" class="wp-image-5001"/>

<p>on the right corner of our mail application click on "more" -> "view source", there we will see our raw htlm texts. Press CTRL + F and type in "return" there we see it filter out Return-Path and showing the sender email.</p> 

<p>Answer to question 1: bounce@rjttznyzjjzydnillquh.designclub.uk.com</p>

<p>#note for .eml file we can use notepad/wordpad/notepad++ to open it and view source</p>

<!-- wp:separator -->
<hr class="wp-block-separator has-alpha-channel-opacity"/>
<!-- /wp:separator -->

<img src="https://github.com/TommyP702/TanPham/assets/169327735/b85d47ce-2bd5-47f4-92a1-511dd0399748" alt="Image from GitHub" class="wp-image-5001">

<p>To find the domain name type in "a href=" in the source view, the "a href=" is a hypertext use in HTLM language to send the victem into a different destination link can could be malicous</p>
<p> Here if you see the text "if you perfer not to receive further communication please unsubscribe"  and the "a href=" , can we determine where the domain for the url will be send back to "https://storage.googleapis.com"</p>

<p>Answer to question 2: storage.googleapis.com </p>


<!-- wp:separator -->
<hr class="wp-block-separator has-alpha-channel-opacity"/>
<!-- /wp:separator -->

<p> lets try to translate what this is saying, we dont have to download any extra addon and just go copy this to your "clipboard" and paste it outside of our VM to google</p>

<img src="https://github.com/TommyP702/TanPham/assets/169327735/844cef58-86c3-4be6-839b-9fd0a145a7b3" alt="Image from GitHub" class="wp-image-5001" width="500" height="500">

<p> is this suspicious? </p>
<p>Question 3: Yes</p>

<!-- wp:separator -->
<hr class="wp-block-separator has-alpha-channel-opacity"/>
<!-- /wp:separator -->

<p>Now can go back to question 2 regarding the url of the mail. Remeber about the "a href=" well we're going to use that url -> copy > paste into virustotal.com</p>

<p>"storage.googleapis.com/hqyoqzatqthj/aemmfcylvxeo.html#QORHNZC44FT4.QORHNZC44FT4?dYCTywfcxr3jcxxrmcdcKBdmc5D6qfcJVcbbb4M"</p>

<img src="https://github.com/TommyP702/TanPham/assets/169327735/d52bfdff-013f-45b0-bff6-75e5610bf072" alt="Image from GitHub" class="wp-image-5001">

<img src="https://github.com/TommyP702/TanPham/assets/169327735/3c67e6d1-5f48-49a8-9b73-e257e01cfff3" alt="Image from GitHub" class="wp-image-5001">

<p>Question 4: SHA-256 = ae71057b738935cb60b60ea62778cdaee35b08534597fb136cbc3feffeff4c22</p>

<p>Question 5: is this a phishing?: yes, reason beside virustotal we can confirm from other osint tools, can we check the =SPF in the header to confirm the SMTP address 134.195.196.43 and the return path are both seprate destination.</p>

<p>"drum roll" Done!</p>








