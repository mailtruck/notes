https://community.segment.com/t/186wd0/wordpress-plugin-deprecated

<div class="topic__main">
    <h1 class="topic__title">WordPress Plugin [Deprecated]</h1>
      <div class="topic-meta-wrap">

    






  

</div>
<div class="cfa topic__text formatted"><p> <em>Official support from Segment for this plugin is deprecated. The current version of this plugin should be free of bugs but any existing and future development will be paused for the time being. We recommend exploring and using third-party alternatives.</em> </p> 
<p> <em><strong>We are currently looking for community maintainers!</strong>&nbsp; If you’re interested in maintaining or contributing to our <a href="https://github.com/segmentio/analytics-wordpress" target="_blank" rel="nofollow">Wordpress plugin</a>, we'll gladly send some Segment swag your way in return for any merged PRs. Don't forget to give us a heads up via <a href="http://segment.com/contact/" target="_blank" rel="nofollow">our contact form</a>&nbsp;when you submit a&nbsp;PR. &nbsp;</em> </p> 
<hr> 
<h2>Overview</h2> 
<p> Our WordPress plugin lets you record analytics from your WordPress site. It uses the client-side&nbsp;<a href="https://segment.com/docs/sources/website/analytics.js" target="_blank" rel="nofollow">Analytics.js</a>&nbsp;routing and takes only a minute to setup! </p> 
<p> The plugin automatically collects page views and identifies users when they log in. You’ll have a basic analytics set up without a single line of code. </p> 
<p> Our plugin even tracks&nbsp;<a href="https://segment.com/docs/sources/website/guides/woocommerce" target="_blank" rel="nofollow">WooCommerce</a>&nbsp;and&nbsp;<a href="https://segment.com/docs/sources/website/guides/wp-ecommerce" target="_blank" rel="nofollow">WP eCommerce</a>&nbsp;events automatically following our<a href="https://segment.com/docs/spec/ecommerce/v2/" target="_blank" rel="nofollow">E-Commerce Tracking Guide</a>. </p> 
<h2 id="getting-started">Getting Started</h2> 
<p> Installing our WordPress plugin is really quick: </p> 
<ol> 
 <li>Go to the&nbsp;<strong>Plugins &gt; Add New</strong>&nbsp;page in your WordPress admin.</li> 
 <li>Search for&nbsp;<strong>Segment</strong>&nbsp;and install&nbsp;<strong>Analytics for WordPress - by Segment</strong>.</li> 
 <li>Click&nbsp;<strong>Activate Plugin</strong>.</li> 
 <li>Click the plugin’s&nbsp;<strong>Settings</strong>&nbsp;button and enter your Segment source’s&nbsp;<strong>Write Key</strong>&nbsp;into the field and hit save.</li> 
</ol> 
<p> That’s it, you’re done! You’ll automatically be identifying users and recording their actions as they move around your WordPress site. </p> 
<p> Now just turn on any of our integrations on your integrations page and we’ll start sending your data to them for you! </p> 
<h2 id="common-questions">Common Questions</h2> 
<h3 id="what-user-information-does-it-record-automatically-">What user information does it record automatically?</h3> 
<p> We automatically track a&nbsp;<strong><code>Logged In</code></strong>&nbsp;event, as well as identify users that are logged in to your WordPress site, and we record their&nbsp;<strong><code>name</code></strong>,&nbsp;<strong><code>email</code></strong>,&nbsp;<strong><code>username</code></strong>, and&nbsp;<strong><code>website</code></strong>, so you don’t need to write any special code to handle that yourself. We also identify commenters if we can. </p> 
<h3 id="which-actions-does-it-record-automatically-">Which actions does it record automatically?</h3> 
<p> Just by installing the plugin, without touching any code, we’ll already be recording events based on the different types of pages the user visits: </p> 
<hr> 
<table> 
 <tbody> 
  <tr> 
   <td><code>Viewed Home Page</code></td> 
   <td> <p> When the user views your home page, whether it’s a static page or a list of recent posts. </p> <p> &nbsp; </p> </td> 
  </tr> 
  <tr> 
   <td><code>Viewed Post</code></td> 
   <td> <p> When the user views a post. If they’re viewing a custom post type, we’ll use its name instead. </p> <p> &nbsp; </p> </td> 
  </tr> 
  <tr> 
   <td> <p> <code>Viewed Author Page</code> </p> <p> &nbsp; </p> </td> 
   <td> <p> When the user views an archive of posts by a specific author. </p> <p> &nbsp; </p> </td> 
  </tr> 
  <tr> 
   <td> <p> <code>Viewed Category Page</code> </p> <p> &nbsp; </p> </td> 
   <td> <p> When the user views an archive of posts in a specific category. </p> <p> &nbsp; </p> </td> 
  </tr> 
  <tr> 
   <td> <p> <code>Viewed Tag Page</code> </p> <p> &nbsp; </p> </td> 
   <td> <p> When the user views an archive of posts with a specific tag. </p> <p> &nbsp; </p> </td> 
  </tr> 
  <tr> 
   <td> <p> <code>Viewed Search Page</code> </p> </td> 
   <td>When the user views the search results page.</td> 
  </tr> 
 </tbody> 
</table> 
<hr> 
<p> We also automatically add useful properties to the events when applicable. For example, the<code>Viewed Search Page</code>&nbsp;event includes a&nbsp;<code>query</code>&nbsp;property of what the user searched for. </p> 
<h2 id="custom-events">Custom Events</h2> 
<p> For the most basic install, you’re already good to go. But if you want to add your own custom tracking to your WordPress code, there are two ways to do it. You can either add javascript directly, or you can use the global PHP&nbsp;<code>Analytics</code>&nbsp;object, which will just render the necessary javascript into your WordPress page. </p> 
<p> Here’s the javascript you would add to track a custom event: </p> 
<pre class="prettyprint"><code>analytics.track('Song Played', {
  seconds: 268,
  artist: 'Kanye West'
});
</code></pre> 
<p> If you prefer to write in PHP in WordPress template, here’s the PHP code to track the exact same custom event: </p> 
<pre class="prettyprint"><code>Analytics::track('Song Played', array(
  'seconds' =&gt; 268,
  'artist' =&gt; 'Kanye West'
));
</code></pre> 
<hr> 
<table> 
 <tbody> 
  <tr> 
   <td> <p> <strong><code>event</code></strong> </p> <p> <em>String</em> </p> <p> &nbsp; </p> </td> 
   <td> <p> &nbsp;The name of the event you’re tracking. We recommend using human- &nbsp;readable names like&nbsp;<code>'Song Played'</code>&nbsp;or&nbsp;<code>'Status Updated'</code>. </p> </td> 
  </tr> 
  <tr> 
   <td> <p> <strong><code>properties</code></strong> </p> <p> <em>Array, optional</em> </p> </td> 
   <td>&nbsp;An array of properties for the event. If the event was&nbsp;<code>'Add Product'</code>, &nbsp;it might have properties like&nbsp;<code>'price'</code>,&nbsp;<code>'product_type'</code>, etc.</td> 
  </tr> 
 </tbody> 
</table> 
<hr> 
<p class="prettyprint"> &nbsp; </p> 
<table> 
 <tbody> 
  <tr> 
   <td>&nbsp;</td> 
   <td>&nbsp;</td> 
  </tr> 
  <tr> 
   <td>&nbsp;</td> 
   <td>&nbsp;</td> 
  </tr> 
 </tbody> 
</table></div>
          <div class="topic__actions posting__actions">
  <span class="inline-like__wrap -sep">
        <span role="button" class="thm-lnk inline-like js-btn-like " data-action="/topic_do/186wd0/like">Upvote</span>
      </span>
    <span class="inline-follow__wrap -sep">
      <span role="button" class="thm-lnk inline-follow js-btn-follow " data-action="/topic_do/186wd0/follow">Follow</span>
    </span>
    </div>
<div class="topic__share -main js-topic__share" data-url="https://community.segment.com/t/186wd0/wordpress-plugin-deprecated" data-text="WordPress Plugin [Deprecated]"></div>
  <div class="share-template">
    <div class="box"><span role="button" class="facebook"><span class="icon facebook_icon"></span></span><span role="button" class="twitter"><span class="icon twitter_icon"></span></span><span role="button" class="googleplus"><span class="icon googleplus_icon"></span></span><span role="button" class="linkedin"><span class="icon linkedin_icon"></span></span><div class="share-total">{total}</div>
    </div>
  </div>

</div>