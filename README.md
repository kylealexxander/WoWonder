<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__html"><h1 id="welcome-to-wowonder-api-documentation">Welcome to WoWonder API documentation!</h1>
<p>You can use our API to access WoWonder API endpoints, which can get information from various features.</p>
<h1 id="getting-started">Getting Started</h1>
<ol>
<li>Please note that most requests require user authorization, for this you only need to send user’s access_token using GET method.</li>
<li>All requests require your site (server_key) that should be sent with each request using POST method, the key can be found in <em><strong>Admin Panel &gt; Mobile &amp; API Settings &gt; Manage API Access Keys &gt; Server Key</strong></em></li>
<li>This is not a public API that can be used by public users, just the site owner can use it to build third party applications.</li>
<li><strong>IMPORTANT: This API can’t be used for marketing purpose or used to sell third party applications.</strong></li>
</ol>
<h2 id="apiget-site-settings">/api/get-site-settings</h2>
<p>Get your site settings / config / information.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-site-settings">http://your-site.com/api/get-site-settings</a></em></p>
<p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "config": [..], // An array of your site information, config etc..
}
</code></pre>
<h2 id="apiauth">/api/auth</h2>
<p>Log in the user and get the access token.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/auth">http://your-site.com/api/auth</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>username</td>
<td>string</td>
<td>User’s username</td>
<td>Yes</td>
</tr>
<tr>
<td>password</td>
<td>string</td>
<td>User’s password</td>
<td>Yes</td>
</tr>
<tr>
<td>timezone</td>
<td>string</td>
<td>User’s timezone</td>
<td>No</td>
</tr>
<tr>
<td>device_id</td>
<td>string</td>
<td>Onesignal Device ID</td>
<td>No</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "access_token": "", // store this, it will be used for all other API calls
  "user_id": "", // authenticated user id
  "timezone": "", // user timezone
}
</code></pre>
<h2 id="apisocial-login">/api/social-login</h2>
<p>Log in the user and get the access token using FB or google.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/social-login">http://your-site.com/api/social-login</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>access_token</td>
<td>string</td>
<td>FB or Google access_token</td>
<td>Yes</td>
</tr>
<tr>
<td>provider</td>
<td>string(facebook, google)</td>
<td>Login site</td>
<td>Yes</td>
</tr>
<tr>
<td>google_key</td>
<td>string</td>
<td>Google API key</td>
<td>Yes if provider = google</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "access_token": "", // store this, it will be used for all other API calls
  "user_id": "", // authenticated user id
  "timezone": "", // user timezone
}
</code></pre>
<h2 id="apicreate-account">/api/create-account</h2>
<p>Create a new user account. and get the access token.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/create-account">http://your-site.com/api/create-account</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>username</td>
<td>string</td>
<td>User’s username</td>
<td>Yes</td>
</tr>
<tr>
<td>password</td>
<td>string</td>
<td>User’s password</td>
<td>Yes</td>
</tr>
<tr>
<td>email</td>
<td>string</td>
<td>User’s email</td>
<td>Yes</td>
</tr>
<tr>
<td>confirm_password</td>
<td>string</td>
<td>User’s confirm password</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "access_token": "", // store this, it will be used for all other API calls
  "user_id": "", // authenticated user id
}
</code></pre>
<h2 id="apiset-browser-cookie">/api/set-browser-cookie</h2>
<p>Log in the user to the browser using access_token.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/set-browser-cookie?access_token=ACCESS_TOKEN">http://your-site.com/api/set-browser-cookie?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>Success repsond:</strong></p>
<pre><code>Redirects to /get_news_feed page.
</code></pre>
<h2 id="apidelete-access-token">/api/delete-access-token</h2>
<p>Log the user out.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/delete-access-token?access_token=ACCESS_TOKEN">http://your-site.com/api/delete-access-token?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
}
</code></pre>
<h2 id="apisend-reset-password-email">/api/send-reset-password-email</h2>
<p>Send password reset email.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/send-reset-password-email?access_token=ACCESS_TOKEN">http://your-site.com/api/send-reset-password-email?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>email</td>
<td>string</td>
<td>User’s Email</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
}
</code></pre>
<h2 id="apiget-user-data">/api/get-user-data</h2>
<p>Get any user data.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-user-data?access_token=ACCESS_TOKEN">http://your-site.com/api/get-user-data?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>user_id</td>
<td>int</td>
<td>Get the data of this user id.</td>
<td>Yes</td>
</tr>
<tr>
<td>fetch</td>
<td>user_data,followers,following,liked_pages,joined_groups</td>
<td>Choose what you would like to get from the user.</td>
<td>At least one key is required.</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  {The keys that are sent in fetch}
}
</code></pre>
<h2 id="apiget-many-users-data">/api/get-many-users-data</h2>
<p>Get mutli users data, for example you can get 20 users data as array in one API call.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-many-users-data?access_token=ACCESS_TOKEN">http://your-site.com/api/get-many-users-data?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>user_ids</td>
<td>string</td>
<td>IDs separated with commas, example: 1,2,3,4,5</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "users": [..] // array
}
</code></pre>
<h2 id="apiget-user-albums">/api/get-user-albums</h2>
<p>Get user’s albums.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-user-albums?access_token=ACCESS_TOKEN">http://your-site.com/api/get-user-albums?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>user_id</td>
<td>int</td>
<td>Get the albums of this user ID.</td>
<td>Yes</td>
</tr>
<tr>
<td>limit</td>
<td>int</td>
<td>Default: 35</td>
<td>No</td>
</tr>
<tr>
<td>offset</td>
<td>int</td>
<td>Get albums before the offset ID</td>
<td>No</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "albums": {..}
}
</code></pre>
<h2 id="apicreate-product">/api/create-product</h2>
<p>Create new product (market system).</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/create-product?access_token=ACCESS_TOKEN">http://your-site.com/api/create-product?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>product_title</td>
<td>string</td>
<td>Product title, min: 2 letters.</td>
<td>Yes</td>
</tr>
<tr>
<td>product_description</td>
<td>string</td>
<td>Product description, min: 2 letters.</td>
<td>Yes</td>
</tr>
<tr>
<td>product_location</td>
<td>string</td>
<td>Product location, min: 2 letters.</td>
<td>Yes</td>
</tr>
<tr>
<td>product_price</td>
<td>int</td>
<td>Product price</td>
<td>Yes</td>
</tr>
<tr>
<td>product_category</td>
<td>int</td>
<td>Product category</td>
<td>Yes</td>
</tr>
<tr>
<td>product_type</td>
<td>int</td>
<td>1 or 0, 1 for used product, 0 for new.</td>
<td>Yes</td>
</tr>
<tr>
<td>images</td>
<td>Stream (File)</td>
<td>Image, (jpg,png,gif,jpeg)</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "product_id": 0, // created product ID
  "product_post_id": 0 // created product post ID
}
</code></pre>
<h2 id="apiget-products">/api/get-products</h2>
<p>Get latest products, or user products.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-products?access_token=ACCESS_TOKEN">http://your-site.com/api/get-products?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>user_id</td>
<td>int</td>
<td>Get the products of this user ID, leave this if you want to get latest products.</td>
<td>No</td>
</tr>
<tr>
<td>limit</td>
<td>int</td>
<td>Default: 35</td>
<td>No</td>
</tr>
<tr>
<td>offset</td>
<td>int</td>
<td>Get albums before the offset ID</td>
<td>No</td>
</tr>
<tr>
<td>category_id</td>
<td>int</td>
<td>Get the products under this category.</td>
<td>No</td>
</tr>
<tr>
<td>keyword</td>
<td>int</td>
<td>Search for products.</td>
<td>No</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "products": {..}
}
</code></pre>
<h2 id="apiget-events">/api/get-events</h2>
<p>Get latest events, or user events.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-events?access_token=ACCESS_TOKEN">http://your-site.com/api/get-events?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>limit</td>
<td>int</td>
<td>Default: 35</td>
<td>No</td>
</tr>
<tr>
<td>offset</td>
<td>int</td>
<td>Get events before the offset ID</td>
<td>No</td>
</tr>
<tr>
<td>my_offset</td>
<td>int</td>
<td>Get my events before the offset ID</td>
<td>No</td>
</tr>
<tr>
<td>fetch</td>
<td>events,my_events</td>
<td>Choose what you would like to get.</td>
<td>At least one key is required.</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  {Keys that are sent in fetch}
}
</code></pre>
<h2 id="apigo-to-event">/api/go-to-event</h2>
<p>Go to event / remove go to event.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/go-to-event?access_token=ACCESS_TOKEN">http://your-site.com/api/go-to-event?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>event_id</td>
<td>int</td>
<td>event ID</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "go_status": "going|not-going"
}
</code></pre>
<h2 id="apiinterest-event">/api/interest-event</h2>
<p>Interest in event / remove interest in event.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/interest-event?access_token=ACCESS_TOKEN">http://your-site.com/api/interest-event?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>event_id</td>
<td>int</td>
<td>event ID</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "interest_status": "interested|not-interested"
}
</code></pre>
<h2 id="apicreate-event">/api/create-event</h2>
<p>Create new events.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/create-event?access_token=ACCESS_TOKEN">http://your-site.com/api/create-event?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>event_name</td>
<td>string</td>
<td>Event name, min: 5 letters.</td>
<td>Yes</td>
</tr>
<tr>
<td>event_location</td>
<td>string</td>
<td>Event location</td>
<td>Yes</td>
</tr>
<tr>
<td>event_description</td>
<td>string</td>
<td>Event description, min: 10 letters.</td>
<td>Yes</td>
</tr>
<tr>
<td>event_start_date</td>
<td>string</td>
<td>Event start date, fromat: YYYY-MM-DD</td>
<td>Yes</td>
</tr>
<tr>
<td>event_end_date</td>
<td>string</td>
<td>Event end date, fromat: YYYY-MM-DD</td>
<td>Yes</td>
</tr>
<tr>
<td>event_start_time</td>
<td>string</td>
<td>Event start time, fromat: 00:00</td>
<td>Yes</td>
</tr>
<tr>
<td>event_end_time</td>
<td>string</td>
<td>Event end time, fromat: 00:00</td>
<td>Yes</td>
</tr>
<tr>
<td>event_cover</td>
<td>stream (image file)</td>
<td>Event cover, jpg, png, gif, jpeg</td>
<td>No</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "event_id": 0, // created event ID
}
</code></pre>
<h2 id="apifollow-user">/api/follow-user</h2>
<p>Follow or unfollow a user.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/follow-user?access_token=ACCESS_TOKEN">http://your-site.com/api/follow-user?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>user_id</td>
<td>int</td>
<td>Who to follow?</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "follow_status": "followed|unfollowed"
}
</code></pre>
<h2 id="apifollow-request-action">/api/follow-request-action</h2>
<p>Accpet or decline follow / friends requests.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/follow-request-action?access_token=ACCESS_TOKEN">http://your-site.com/api/follow-request-action?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>user_id</td>
<td>int</td>
<td>Who to accept or decline?</td>
<td>Yes</td>
</tr>
<tr>
<td>request_action</td>
<td>accept, decline</td>
<td>Use accpet to accept the follow request, use decline to delete it.</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
}
</code></pre>
<h2 id="apiblock-user">/api/block-user</h2>
<p>Block or unblock a user.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/block-user?access_token=ACCESS_TOKEN">http://your-site.com/api/block-user?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>user_id</td>
<td>int</td>
<td>Who to block or un-block?</td>
<td>Yes</td>
</tr>
<tr>
<td>block_action</td>
<td>block, un-block</td>
<td>Use <strong>block</strong> to block the user, use <strong>un-block</strong> to unblock the user.</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "block_status": "un-blocked|blocked"
}
</code></pre>
<h2 id="apipost-actions">/api/post-actions</h2>
<p>Edit, delete a post | comment, like, wonder|dislike a post.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/post-actions?access_token=ACCESS_TOKEN">http://your-site.com/api/post-actions?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>post_id</td>
<td>int</td>
<td>The post you want to modify</td>
<td>Yes</td>
</tr>
<tr>
<td>action</td>
<td>edit,delete,commet,like,dislike,wonder</td>
<td>…</td>
<td>Yes</td>
</tr>
<tr>
<td>text</td>
<td>string</td>
<td>The post’s or comment’s text</td>
<td>Required if action = <strong>edit</strong> or <strong>comment</strong></td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "action": "deleted|edited|commented|liked|disliked|wondered",
  // if there is comments
  "comment_data": {
    "text": "COMMENT_TEXT",
    "post_comments_count": "COMMENT_COUNT"
   }
}
</code></pre>
<h2 id="apilike-page">/api/like-page</h2>
<p>Like or remove a like from a page.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/like-page?access_token=ACCESS_TOKEN">http://your-site.com/api/like-page?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>page_id</td>
<td>int</td>
<td>The page id you want to like/dislike</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "like_status": "liked|unliked"
}
</code></pre>
<h2 id="apijoin-group">/api/join-group</h2>
<p>Join or leave a group.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/join-group?access_token=ACCESS_TOKEN">http://your-site.com/api/join-group?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>group_id</td>
<td>int</td>
<td>The group id you want to join/leave</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "join_status": "joined|left"
}
</code></pre>
<h2 id="apicreate-story">/api/create-story</h2>
<p>Create new user story.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/create-story?access_token=ACCESS_TOKEN">http://your-site.com/api/create-story?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>story_title</td>
<td>string</td>
<td>Story title, min: 2 letters.</td>
<td>No</td>
</tr>
<tr>
<td>story_description</td>
<td>string</td>
<td>Story description</td>
<td>No</td>
</tr>
<tr>
<td>file</td>
<td>Stream (File)</td>
<td>Images or videos, (jpg,png,mp4,gif,jpeg,mov,webm)</td>
<td>Yes</td>
</tr>
<tr>
<td>file_type</td>
<td>image,video</td>
<td>Use <strong>image</strong> if you are uploading an image, use <strong>video</strong> if you are uploading a video</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "story_id": 0, // created story ID
}
</code></pre>
<h2 id="apidelete-story">/api/delete-story</h2>
<p>Delete user story/status.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/delete-story?access_token=ACCESS_TOKEN">http://your-site.com/api/delete-story?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>story_id</td>
<td>int</td>
<td>Story ID that will be deleted.</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "message": ".."
}
</code></pre>
<h2 id="apiset-chat-typing-status">/api/set-chat-typing-status</h2>
<p>Set chat “typing…” or remove it from chat.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/set-chat-typing-status?access_token=ACCESS_TOKEN">http://your-site.com/api/set-chat-typing-status?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>user_id</td>
<td>int</td>
<td>User ID that the user is chatting with</td>
<td>Yes</td>
</tr>
<tr>
<td>status</td>
<td>typing,stopped</td>
<td>Use typing to show <strong>typing</strong> message on user’s chat box, use <strong>stopped</strong> to remove it.</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
}
</code></pre>
<h2 id="apichange-chat-color">/api/change-chat-color</h2>
<p>Change the chat conversation color.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/change-chat-color?access_token=ACCESS_TOKEN">http://your-site.com/api/change-chat-color?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>user_id</td>
<td>int</td>
<td>User ID that the user is chatting with</td>
<td>Yes</td>
</tr>
<tr>
<td>color</td>
<td>#{COLOR}</td>
<td>Hex color, example: #ffffff</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
}
</code></pre>
<h2 id="apiget-articles">/api/get-articles</h2>
<p>Get latest or user’s articles.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-articles?access_token=ACCESS_TOKEN">http://your-site.com/api/get-articles?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>limit</td>
<td>int</td>
<td>Default: 25</td>
<td>No</td>
</tr>
<tr>
<td>offset</td>
<td>int</td>
<td>Get articles after the offset ID</td>
<td>No</td>
</tr>
<tr>
<td>user_id</td>
<td>int</td>
<td>Filter by user.</td>
<td>No</td>
</tr>
<tr>
<td>category</td>
<td>int</td>
<td>Filter by category.</td>
<td>No</td>
</tr>
<tr>
<td>article_id</td>
<td>int</td>
<td>Get a specified article by ID.</td>
<td>No</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "articles": [..] // Array
}
</code></pre>
<h2 id="apiget-group-data">/api/get-group-data</h2>
<p>Get any group data.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-group-data?access_token=ACCESS_TOKEN">http://your-site.com/api/get-group-data?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>group_id</td>
<td>int</td>
<td>Get the data of this group.</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "group_data": {..} // Object
}
</code></pre>
<h2 id="apiget-page-data">/api/get-page-data</h2>
<p>Get any page data.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-page-data?access_token=ACCESS_TOKEN">http://your-site.com/api/get-page-data?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>page_id</td>
<td>int</td>
<td>Get the data of this page.</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "page_data": {..} // Object
}
</code></pre>
<h2 id="get_news_feed">/get_news_feed</h2>
<p>An HTML hybird page that displays user’s latest posts, page’s posts , group’s posts and latest timeline posts.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/get_news_feed">http://your-site.com/get_news_feed</a></em></p>
<p><strong>GET data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>user_id</td>
<td>Show posts of this ID</td>
<td>Get the data of this post.</td>
<td>No</td>
</tr>
<tr>
<td>page_id</td>
<td>Show posts of this page</td>
<td>Get the data of this post.</td>
<td>No</td>
</tr>
<tr>
<td>group_id</td>
<td>Show posts of this group</td>
<td>Get the data of this post.</td>
<td>No</td>
</tr>
</tbody>
</table><p><strong>Output:</strong></p>
<p>HTML Document.</p>
<h2 id="apiget-post-data">/api/get-post-data</h2>
<p>Get any post data.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-post-data?access_token=ACCESS_TOKEN">http://your-site.com/api/get-post-data?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>post_id</td>
<td>int</td>
<td>Get the data of this post.</td>
<td>Yes</td>
</tr>
<tr>
<td>fetch</td>
<td>post_data,post_comments,post_wondered_users,post_liked_users</td>
<td>Choose what you would like to get from the post.</td>
<td>At least one key is required.</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  {Keys that are sent in fetch}
}
</code></pre>
<h2 id="apiupdate-user-data">/api/update-user-data</h2>
<p>Update user data, avatar, cover, general settings, privacy and a lot more.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/update-user-data?access_token=ACCESS_TOKEN">http://your-site.com/api/update-user-data?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>username</td>
<td>string</td>
<td>User’s username</td>
<td>No</td>
</tr>
<tr>
<td>email</td>
<td>string</td>
<td>User’s email address</td>
<td>No</td>
</tr>
<tr>
<td>phone_number</td>
<td>string</td>
<td>User’s phone number</td>
<td>No</td>
</tr>
<tr>
<td>new_password</td>
<td>string</td>
<td>User’s new_password</td>
<td>No</td>
</tr>
<tr>
<td>current_password</td>
<td>string</td>
<td>User’s current password</td>
<td>Yes, if new password is sent.</td>
</tr>
<tr>
<td>gender</td>
<td>string (male, female)</td>
<td>User’s gender</td>
<td>No</td>
</tr>
<tr>
<td>avatar</td>
<td>Stream (File)</td>
<td>User’s profile picture</td>
<td>No</td>
</tr>
<tr>
<td>cover</td>
<td>Stream (File</td>
<td>User’s profile avatar</td>
<td>No</td>
</tr>
<tr>
<td>…</td>
<td>strings</td>
<td>You can use and update any user data by sending the key name with its value in the POST request as above.</td>
<td>No</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "message": "Your profile was updated"
}
</code></pre>
<h2 id="apiupdate-group-data">/api/update-group-data</h2>
<p>Update group data, avatar, cover, general settings, privacy and a lot more.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/update-group-data?access_token=ACCESS_TOKEN">http://your-site.com/api/update-group-data?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>group_id</td>
<td>string</td>
<td>Effected group ID</td>
<td>Yes</td>
</tr>
<tr>
<td>group_name</td>
<td>string</td>
<td>Group name</td>
<td>No</td>
</tr>
<tr>
<td>group_title</td>
<td>string</td>
<td>Group title</td>
<td>No</td>
</tr>
<tr>
<td>about</td>
<td>string</td>
<td>Group description</td>
<td>No</td>
</tr>
<tr>
<td>category</td>
<td>string</td>
<td>Category ID</td>
<td>No</td>
</tr>
<tr>
<td>privacy</td>
<td>1,0</td>
<td>Public or Private</td>
<td>No</td>
</tr>
<tr>
<td>avatar</td>
<td>Stream (File)</td>
<td>User’s profile picture</td>
<td>No</td>
</tr>
<tr>
<td>cover</td>
<td>Stream (File)</td>
<td>User’s profile avatar</td>
<td>No</td>
</tr>
<tr>
<td>…</td>
<td>strings</td>
<td>You can use and update any user data by sending the key name with its value in the POST request as above.</td>
<td>No</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "message": "Your group was updated"
}
</code></pre>
<h2 id="apiupdate-page-data">/api/update-page-data</h2>
<p>Update page data, avatar, cover, general settings, privacy and a lot more.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/update-page-data?access_token=ACCESS_TOKEN">http://your-site.com/api/update-page-data?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>page_id</td>
<td>string</td>
<td>Effected page ID</td>
<td>Yes</td>
</tr>
<tr>
<td>page_name</td>
<td>string</td>
<td>Page name</td>
<td>No</td>
</tr>
<tr>
<td>page_title</td>
<td>string</td>
<td>Page title</td>
<td>No</td>
</tr>
<tr>
<td>page_description</td>
<td>string</td>
<td>Page description</td>
<td>No</td>
</tr>
<tr>
<td>page_category</td>
<td>string</td>
<td>Category ID</td>
<td>No</td>
</tr>
<tr>
<td>avatar</td>
<td>Stream (File)</td>
<td>User’s profile picture</td>
<td>No</td>
</tr>
<tr>
<td>cover</td>
<td>Stream (File)</td>
<td>User’s profile avatar</td>
<td>No</td>
</tr>
<tr>
<td>…</td>
<td>strings</td>
<td>You can use and update any user data by sending the key name with its value in the POST request as above.</td>
<td>No</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "message": "Your page was updated"
}
</code></pre>
<h2 id="apiget-movies">/api/get-movies</h2>
<p>Get latest movies.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-movies?access_token=ACCESS_TOKEN">http://your-site.com/api/get-movies?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>limit</td>
<td>int</td>
<td>Movies Limit</td>
<td>No</td>
</tr>
<tr>
<td>id</td>
<td>int</td>
<td>Get movie information for this ID</td>
<td>No</td>
</tr>
<tr>
<td>offset</td>
<td>int</td>
<td>get movies after this ID</td>
<td>No</td>
</tr>
<tr>
<td>genre</td>
<td>string</td>
<td>get movies under this genre category</td>
<td>No</td>
</tr>
<tr>
<td>country</td>
<td>string</td>
<td>get movies under this country</td>
<td>No</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "movies": [] // Array of latest movies
}
</code></pre>
<h2 id="apicreate-group">/api/create-group</h2>
<p>Create a new group. and get the created group data.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/create-group?access_token=ACCESS_TOKEN">http://your-site.com/api/create-group?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>group_name</td>
<td>string</td>
<td>Group name without special characters</td>
<td>Yes</td>
</tr>
<tr>
<td>group_title</td>
<td>string</td>
<td>Group title</td>
<td>Yes</td>
</tr>
<tr>
<td>about</td>
<td>string</td>
<td>Group about info</td>
<td>Yes</td>
</tr>
<tr>
<td>category</td>
<td>int</td>
<td>Category ID</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "group_data": {..} // Object data of the created group
}
</code></pre>
<h2 id="apicreate-page">/api/create-page</h2>
<p>Create a new page. and get the created page data.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/create-page?access_token=ACCESS_TOKEN">http://your-site.com/api/create-page?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>page_name</td>
<td>string</td>
<td>Page name without special characters</td>
<td>Yes</td>
</tr>
<tr>
<td>page_title</td>
<td>string</td>
<td>Page title</td>
<td>Yes</td>
</tr>
<tr>
<td>page_category</td>
<td>string</td>
<td>Page about info</td>
<td>Yes</td>
</tr>
<tr>
<td>page_description</td>
<td>string</td>
<td>Category ID</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "page_data": {..} // Object data of the created group
}   
</code></pre>
<h2 id="apiget-nearby-users">/api/get-nearby-users</h2>
<p>Get nearby users using lat / lng</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-nearby-users?access_token=ACCESS_TOKEN">http://your-site.com/api/get-nearby-users?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>limit</td>
<td>int</td>
<td>Default: 25</td>
<td>No</td>
</tr>
<tr>
<td>offset</td>
<td>int</td>
<td>Get articles after the offset ID</td>
<td>No</td>
</tr>
<tr>
<td>gender</td>
<td>male,female</td>
<td>Filter by gender.</td>
<td>No</td>
</tr>
<tr>
<td>keyword</td>
<td>string</td>
<td>Filter by name.</td>
<td>No</td>
</tr>
<tr>
<td>status</td>
<td>1,0</td>
<td>Filter by online / offline.</td>
<td>No</td>
</tr>
<tr>
<td>distance</td>
<td>int</td>
<td>Filter by distance / km</td>
<td>No</td>
</tr>
<tr>
<td>lat</td>
<td>string</td>
<td>Update user lat</td>
<td>No</td>
</tr>
<tr>
<td>lng</td>
<td>string</td>
<td>Update user lng</td>
<td>No</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "nearby_users": [..] // Array
}
</code></pre>
<h2 id="apiget-blocked-users">/api/get-blocked-users</h2>
<p>Get blocked users.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-blocked-users?access_token=ACCESS_TOKEN">http://your-site.com/api/get-blocked-users?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "blocked_users": [..] // Array
}   
</code></pre>
<h2 id="apiget-stories">/api/get-stories</h2>
<p>Get latest friends stories.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-stories?access_token=ACCESS_TOKEN">http://your-site.com/api/get-stories?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>limit</td>
<td>int</td>
<td>Default: 25</td>
<td>No</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "stories": [..] // Array
}
</code></pre>
<h2 id="apidelete-conversation">/api/delete-conversation</h2>
<p>Delete chat conversation</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/delete-conversation?access_token=ACCESS_TOKEN">http://your-site.com/api/delete-conversation?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>user_id</td>
<td>int</td>
<td>User id you want to delete the conversation with.</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "message": ".."
}
</code></pre>
<h2 id="apiget-community">/api/get-community</h2>
<p>Get user’s owned groups &amp; pages.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-community?access_token=ACCESS_TOKEN">http://your-site.com/api/get-community?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>user_id</td>
<td>int</td>
<td>Get the data of this user ID.</td>
<td>Yes</td>
</tr>
<tr>
<td>fetch</td>
<td>groups,pages</td>
<td>At least one key is required.</td>
<td></td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  {Keys that are sent in fetch}
}
</code></pre>
<h2 id="apiget-general-data">/api/get-general-data</h2>
<p>Get general site &amp; user data, notification, friend/follow requests, counts, hashtags, pro users, and promoted pages</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-general-data?access_token=ACCESS_TOKEN">http://your-site.com/api/get-general-data?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>fetch</td>
<td>notifications,friend_requests,pro_users,promoted_pages,trending_hashtag,count_new_messages</td>
<td>At least one key is required.</td>
<td></td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  {Keys that are sent in fetch}
}
</code></pre>
<h2 id="apiget-user-suggestions">/api/get-user-suggestions</h2>
<p>Get random users to follow, or get users that matchs phone numbers.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-user-suggestions?access_token=ACCESS_TOKEN">http://your-site.com/api/get-user-suggestions?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>contacts</td>
<td>json string</td>
<td>Get users that matchs those phone numbers, example: [NUMBER1, NUMBER2].</td>
<td>No</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "suggestions": [],
  "contacts_suggestions": []
}.
</code></pre>
<h2 id="apisend-message">/api/send-message</h2>
<p>Send a message to a user (file, sticker, or text)</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/send-message?access_token=ACCESS_TOKEN">http://your-site.com/api/send-message?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>user_id</td>
<td>int</td>
<td>To whom this message is sent</td>
<td>Yes</td>
</tr>
<tr>
<td>message_hash_id</td>
<td>int</td>
<td>Generate a random unique hash, so you can use after the message is sent.</td>
<td>Yes</td>
</tr>
<tr>
<td>text</td>
<td>string</td>
<td>Message text.</td>
<td>No</td>
</tr>
<tr>
<td>file</td>
<td>stream (File)</td>
<td>Attach a file to the message.</td>
<td>No</td>
</tr>
<tr>
<td>image_url</td>
<td>string (URL)</td>
<td>Import an image from a url.</td>
<td>No</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "message_data": [..] // Array
}
</code></pre>
<h2 id="apisearch">/api/search</h2>
<p>Search for users, pages, groups</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/search?access_token=ACCESS_TOKEN">http://your-site.com/api/search?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>limit</td>
<td>int</td>
<td>Default: 35</td>
<td>No</td>
</tr>
<tr>
<td>user_offset</td>
<td>int</td>
<td>Get users before the offset ID</td>
<td>No</td>
</tr>
<tr>
<td>page_offset</td>
<td>int</td>
<td>Get paes before the offset ID</td>
<td>No</td>
</tr>
<tr>
<td>group_offset</td>
<td>int</td>
<td>Get groups before the offset ID</td>
<td>No</td>
</tr>
<tr>
<td>gender</td>
<td>string</td>
<td>Filter by gender (male/female)</td>
<td>No</td>
</tr>
<tr>
<td>search_key</td>
<td>string</td>
<td>Keyword.</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
   "api_status": 200,
   "users": [],
   "pages": [],
   "groups": []
}
</code></pre>
<h2 id="apiget-activities">/api/get-activities</h2>
<p>Get latest activities</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/get-activities?access_token=ACCESS_TOKEN">http://your-site.com/api/get-activities?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>limit</td>
<td>int</td>
<td>Default: 25</td>
<td>No</td>
</tr>
<tr>
<td>offset</td>
<td>int</td>
<td>Get activities before the offset ID</td>
<td>No</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
   "api_status": 200,
   "activities": [],
}
</code></pre>
<h2 id="apidelete-user">/api/delete-user</h2>
<p>Delete user.</p>
<p><em><em>End point:</em> <a href="http://your-site.com/api/delete-user?access_token=ACCESS_TOKEN">http://your-site.com/api/delete-user?access_token=ACCESS_TOKEN</a></em></p>
<p><strong>POST data:</strong></p>

<table>
<thead>
<tr>
<th>Key</th>
<th>Value</th>
<th>Description</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>password</td>
<td>string</td>
<td>User’s Password.</td>
<td>Yes</td>
</tr>
</tbody>
</table><p><strong>JSON formatted success repsond:</strong></p>
<pre><code>{
  "api_status": 200,
  "message": "User successfully deleted."
}
</code></pre>
<h1 id="error-handling">Error Handling</h1>
<p>All endpoints errors respond looks like:</p>
<pre><code>{
  "api_status": "400",
  "errors": {
      "error_id": ID,
      "error_text": "..."
  }
}
</code></pre>
</div>
</body>

</html>
