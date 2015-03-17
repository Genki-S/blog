---
title: How to Get PUSH Notification from GitHub
layout: post
permalink: /how-to-get-push-notification-from-github/
dsq_thread_id:
  - 2624944856
categories:
  - Uncategorized
tags:
  - github
  - productivity
---
If you use GitHub for your job or for your hobby, it&#8217;s likely that sometimes you have to wait other people to review your code or comment on issues. One day, I realized myself visiting GitHub every so often so that I can notice reviews as soon as possible. I knew this is really bad for my productivity because it meant I was using my brain resources just waiting for other people.

So, I have set up a system which sends push notifications when I get comments on GitHub. This system is to my previous GitHub checking habit what <a href="http://en.wikipedia.org/wiki/Interrupt" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://en.wikipedia.org']);">Interrupt</a> is to <a href="http://en.wikipedia.org/wiki/Polling_(computer_science)" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://en.wikipedia.org']);">Polling</a> in computer science &#x2013; huge improvement in terms of using CPU (my brain) efficiently. I will share this system for you.

This post assumes following situations:

<ul class="org-ul">
  <li>
    You have a Gmail account
  </li>
  <li>
    You are not getting push notifications for emails (if you are, I must tell you that those are &#8220;<a href="http://lifehacker.com/5895617/you-should-forget-about-push-notifications-for-your-email" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://lifehacker.com']);">killing your focus and destroying your ability to work to your capacity</a>&#8220;)
  </li>
  <li>
    You know what IFTTT is (if not, I highly recommend you to <a href="http://www.quickanddirtytips.com/tech/web/what-is-ifttt-and-how-can-it-improve-your-digital-life" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://www.quickanddirtytips.com']);">learn what it is and how it can improve your digital life</a>)
  </li>
</ul>

<div id="outline-container-sec-1" class="outline-2">
  <h2 id="sec-1">
    GitHub&#8217;s Notification
  </h2>

  <div class="outline-text-2" id="text-1">
    <p>
      You might be thinking, &#8220;don&#8217;t you know GitHub already provides notification service?&#8221; I know it, but the problem is that it only provides email notification. To be precise, my habit was to check Gmail every so often so that I can notice GitHub notification, which was killing my productivity. Email is not the way to get important notifications because other non-important emails might catch your eye and distract you.
    </p>

    <p>
      So, the goal of the system is to somehow turn GitHub&#8217;s email notification into push notification.
    </p></p>
  </div></p>
</div>

<div id="outline-container-sec-2" class="outline-2">
  <h2 id="sec-2">
    IFTTT
  </h2>

  <div class="outline-text-2" id="text-2">
    <p>
      This is where IFTTT comes in. Let&#8217;s create a new recipe which will be triggered by emails from GitHub and send you push notifications. The recipe I created is <a href="https://ifttt.com/myrecipes/personal/9646882" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://ifttt.com']);">here</a> and you can see it as an example (or just use it directly).
    </p></p>
  </div>

  <div id="outline-container-sec-2-1" class="outline-3">
    <h3 id="sec-2-1">
      This: Email with Label
    </h3>

    <div class="outline-text-3" id="text-2-1">
      <p>
        Choose Gmail as a trigger channel, and choose &#8220;New email labeled&#8221; as a trigger. Any label name would work, but make it clear like &#8220;github&#8221;. I will explain how to label emails later.
      </p></p>
    </div></p>
  </div>

  <div id="outline-container-sec-2-2" class="outline-3">
    <h3 id="sec-2-2">
      That: Notification
    </h3>

    <div class="outline-text-3" id="text-2-2">
      <p>
        Any notification service would work. My choice for now is <a href="https://www.pushbullet.com/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://www.pushbullet.com']);">Pushbullet</a>. I am not a heavy user yet, but I like the simple interface and it is doing its job so far on my Firefox and iPod touch. After you choose your notification service, create push content using Gmail&#8217;s ingredients like &#8220;Subject&#8221; and &#8220;BodyPlain&#8221;.
      </p></p>
    </div></p>
  </div></p>
</div>

<div id="outline-container-sec-3" class="outline-2">
  <h2 id="sec-3">
    Label Emails from GitHub
  </h2>

  <div class="outline-text-2" id="text-3">
    <p>
      Now you should be able to get notification whenever an email is labeled &#8220;github&#8221;. So, the last step is to label GitHub notification emails.
    </p></p>
  </div>

  <div id="outline-container-sec-3-1" class="outline-3">
    <h3 id="sec-3-1">
      Change GitHub&#8217;s Notification Address
    </h3>

    <div class="outline-text-3" id="text-3-1">
      <p>
        Gmail offers a pretty awesome trick that you can <a href="http://gmailblog.blogspot.jp/2008/03/2-hidden-ways-to-get-more-from-your.html" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://gmailblog.blogspot.jp']);">append &#8220;+&#8221; and any text after your email address&#8217; local part</a>. If your address is &#8220;mail@gmail.com&#8221;, you can use addresses like &#8220;mail+friends@gmail.com&#8221; or &#8220;mail+family@gmail.com&#8221;, and as you guessed, &#8220;mail+github@gmail.com&#8221; too. So, let&#8217;s make GitHub send notifications to your &#8220;mail+github@gmail.com&#8221; address.
      </p>

      <ol class="org-ol">
        <li>
          Add another email address (&#8220;mail+github@gmail.com&#8221;): <a href="https://github.com/settings/emails" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">https://github.com/settings/emails</a>
        </li>
        <li>
          Choose that as the notification email address: <a href="https://github.com/settings/notifications" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">https://github.com/settings/notifications</a>
        </li>
      </ol>
    </div></p>
  </div>

  <div id="outline-container-sec-3-2" class="outline-3">
    <h3 id="sec-3-2">
      Create a Filter
    </h3>

    <div class="outline-text-3" id="text-3-2">
      <p>
        Now, let&#8217;s assign the &#8220;github&#8221; label to all emails sent to &#8220;mail+github@gmail.com&#8221; address.
      </p>

      <ol class="org-ol">
        <li>
          Visit <a href="https://mail.google.com/mail/u/0/#settings/filters" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://mail.google.com']);">https://mail.google.com/mail/u/0/#settings/filters</a>
        </li>
        <li>
          Click &#8220;Create a new filter&#8221;
        </li>
        <li>
          Input &#8220;mail+github@gmail.com&#8221; to &#8220;To&#8221; field
        </li>
        <li>
          Click &#8220;Create filter with this search&#8221;
        </li>
        <li>
          In &#8220;Apply the label&#8221; section, choose &#8220;github&#8221; (you can create new label here. Be sure to choose the same name you used in your IFTTT recipe)
        </li>
        <li>
          Click &#8220;Create filter&#8221;
        </li>
      </ol>
    </div></p>
  </div></p>
</div>

<div id="outline-container-sec-4" class="outline-2">
  <h2 id="sec-4">
    All Set
  </h2>

  <div class="outline-text-2" id="text-4">
    <p>
      OK, you are all set and now you can forget about waiting for code reviews or comments and do other productive things until push notifications come. But before that, I recommend you to test your system by sending an email to &#8220;mail+github@gmail.com&#8221; yourself. The mail should be labeled as &#8220;github&#8221; and push notification should be sent to you. (In my case, it took 2 to 3 minutes to get a push after sending an email myself, so don&#8217;t worry if your push does not come instantly.)
    </p></p>
  </div></p>
</div>

<div id="outline-container-sec-5" class="outline-2">
  <h2 id="sec-5">
    What&#8217;s Next?
  </h2>

  <div class="outline-text-2" id="text-5">
    <p>
      This technique can be applied to any situations. For example, you can get notifications for emails from your family by having them send emails to &#8220;mail+family@gmail.com&#8221; rather than &#8220;mail@gmail.com&#8221; (don&#8217;t forget to create another IFTTT recipe and another Gmail filter). Push notification can help you free up your brain resources like this, or hurt your productivity by distracting you all the time. So, push wisely.
    </p></p>
  </div></p>
</div>
