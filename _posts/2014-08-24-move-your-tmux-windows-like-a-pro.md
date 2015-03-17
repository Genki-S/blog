---
title: Move Your Tmux Windows like a Pro
layout: post
permalink: /move-your-tmux-windows-like-a-pro/
dsq_thread_id:
  - 2954523091
dsq_needs_sync:
  - 1
categories:
  - Uncategorized
tags:
  - productivity
  - tmux
---
<a href="http://tmux.sourceforge.net/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://tmux.sourceforge.net']);">tmux</a> is a great tool for us programmers. However, there are some frustrations about it. One of them is its inability to move windows intuitively. In this post, I&#8217;m going to give you a script and key bindings which enable you to move tmux windows around like a pro.

<div id="outline-container-sec-1" class="outline-2">
  <h2 id="sec-1">
    How you move windows
  </h2>

  <div class="outline-text-2" id="text-1">
    <p>
      Without any scripting, you can move windows using tmux&#8217;s <code>tmux swap-window</code> command. It takes <code>-s</code> (source) and <code>-t</code> (target) options, and (you guessed it) swap them. So for example, if you want to swap windows 2 and 5, you type:
    </p>

    <div class="org-src-container">
      <pre class="src src-sh">$ tmux swap-window -s :2 -t :5
</pre>
    </div>

    <p>
      This is a little fingerful. And I generally don&#8217;t &#8220;swap&#8221; windows, I just move it (think about when you move tabs on your web browser). So, while above commands make window arrangement from &#8220;1 2 3 4 5&#8243; to &#8220;1 5 3 4 2&#8243;, what I really want is &#8220;1 3 4 5 2&#8243;, like when I moved 2nd tab to the right of 5th tab in my web browser.
    </p>
  </div>
</div>

<div id="outline-container-sec-2" class="outline-2">
  <h2 id="sec-2">
    Solution &#x2013; script
  </h2>

  <div class="outline-text-2" id="text-2">
    <p>
      Fortunately, tmux is highly scriptable. So with a little effort, you can get the behavior you want. For the purpose of moving windows, I wrote the script below:
    </p>

    <p>
      <code data-gist-id='488b3d38cd93f88e3525'></code>
    </p>

    <p>
      What it does is to just swap adjacent windows, considering wrapping. So, if you want to move current window to right, (assuming you have the script in your PATH) you can type:
    </p>

    <div class="org-src-container">
      <pre class="src src-sh">$ tmux-win-move right
</pre>
    </div>

    <p>
      On 2nd window of &#8220;1 2 3 4 5&#8243; arrangement, by repeating this command 3 times, you can get desired &#8220;1 3 4 5 2&#8243; arrangement. However, repeating such a command is tedious. This is where key binding comes in.
    </p>
  </div>
</div>

<div id="outline-container-sec-3" class="outline-2">
  <h2 id="sec-3">
    Solution &#x2013; key binding
  </h2>

  <div class="outline-text-2" id="text-3">
    <p>
      If you are a vim user, I recommend you to put the following bindings in your <code>~/.tmux.conf</code>:
    </p>

    <div class="org-src-container">
      <pre class="src src-sh">bind-key -r H run-shell <span style="color: #00afaf;">'tmux-win-move left'</span>
bind-key -r L run-shell <span style="color: #00afaf;">'tmux-win-move right'</span>
</pre>
    </div>

    <p>
      <code>-r</code> option makes the key binding repeatable, meaning that you can repeat above command by (if your prefix is C-b) <code>C-b L L L</code> if you type it fast enough.
    </p>

    <p>
      So, with above script and key bindings, you can move your tmux windows like a pro. After using it myself for a while, I&#8217;m pretty fond of it. It feels like the same as moving tabs on web browsers, so I know intuitively what the arrangement will look like after I move a window.
    </p>
  </div>
</div>

<div id="outline-container-sec-4" class="outline-2">
  <h2 id="sec-4">
    What&#8217;s next?
  </h2>

  <div class="outline-text-2" id="text-4">
    <p>
      Now that you can move tmux windows as you like, you have no reason to be afraid of having many windows. In order to make it easy to generate many windows, I recommend <a href="https://github.com/tmuxinator/tmuxinator" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">tmuxinator gem</a>. It makes development setup (e.g. <code>mysqld start</code>, <code>rails server</code> etc.) a snap.
    </p>
  </div>
</div>
