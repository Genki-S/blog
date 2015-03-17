---
title: Use imap Wisely to Boost Your Programming Speed
layout: post
permalink: /use-imap-wisely-to-boost-your-programming-speed/
dsq_thread_id:
  - 2557543376
categories:
  - Uncategorized
tags:
  - vim
---
In some programming languages, there are some codes which are difficult to type. For example, in Ruby, hashrocket (`​=>`) is one of such codes. These codes not only make us slow to program, but also interrupts our concentration because we have to use some brain resource just to type these codes. Thus, these codes should be made easy to type so that our flows will not be interrupted. Here is how I do it.

<div id="outline-container-sec-1" class="outline-2">
  <h2 id="sec-1">
    Use imap, but Wisely
  </h2>

  <div class="outline-text-2" id="text-1">
    <p>
      <code>imap</code> is useful, but it can mess your programming experience if you use it mindlessly. I use <code>&lt;Leader&gt;&lt;C-something&gt;</code> for insert mode mappings so that I don&#8217;t get unwanted behavior when I just want to input normal texts.
    </p>

    <p>
      Here is how I make inputting hashrocket easy (in <code>~/.vim/ftplugin/ruby.vim</code>):
    </p>

    <p>
      <code data-gist-id='9879379'></code>

      <p>
        <code>&lt;C-l&gt;</code> stands for &#8216;right&#8217;, because <code>​=&gt;</code> looks like a right arrow. By using this, I can input <code>&lt;Leader&gt;&lt;C-l&gt;</code> instead of <code>&lt;Space&gt;=&gt;&lt;Space&gt;</code> when I want to input hashrocket.
      </p>

      <p>
        For C++, I use this similar mappings:
      </p>

      <p>
        <code data-gist-id='9879471'></code>

        <p>
          This makes it easy to use streams like <code>cin &gt;&gt; var</code> and <code>cout &lt;&lt; var &lt;&lt; endl;</code>.
        </p>
      </p></div>
    </p>
  </div>

  <div id="outline-container-sec-2" class="outline-2">
    <h2 id="sec-2">
      What&#8217;s Next?
    </h2>

    <div class="outline-text-2" id="text-2">
      <p>
        You might prefer to use <a href="https://github.com/kana/vim-smartchr" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">vim-smartchr</a> rather than <code>imap</code>. It allows you to change inputs based on how many times you type certain keys in insert mode. For example, when you set vim-smartchr as follows, you can hit <code>​=​</code> three times in insert mode to get a hashrocket with spaces around it:
      </p>

      <p>
        <code data-gist-id='9881232'></code>

        <p>
          I used to use it, but I could not adopt to it well&#x2026; I had to use my brain resource (i.e. think) in order to get the code I wanted.
        </p>
      </p>
    </div></p>
  </div>
