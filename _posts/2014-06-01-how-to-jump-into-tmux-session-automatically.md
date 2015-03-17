---
title: How to Jump into Tmux Session Automatically
layout: post
permalink: /how-to-jump-into-tmux-session-automatically/
dsq_thread_id:
  - 2727613847
categories:
  - Uncategorized
tags:
  - productivity
  - shell
  - tmux
---
<a href="http://tmux.sourceforge.net/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://tmux.sourceforge.net']);">Tmux</a> is a very powerful tool to boost your productivity. It became one of my most important tools shortly after I start using it. I can&#8217;t imagine how I was working when I didn&#8217;t know about tmux.

Previously, I was using iTerm&#8217;s &#8220;Send text at start&#8221; feature to invoke tmux session automatically. However, one day, when I was playing with my Linux machine, I noticed I was not in tmux session when I tried to scroll up and see what was the output of the previous command. This really irritated me and I thought I had to do something about it. Today, I&#8217;ll share what I did so that I can always be in tmux session.

<div id="outline-container-sec-1" class="outline-2">
  <h2 id="sec-1">
    The Right Place to Start Tmux Session: ~/.zshrc
  </h2>

  <div class="outline-text-2" id="text-1">
    <p>
      Fortunately, tmux is highly scriptable. This makes it possible to automate many aspects of tmux controls by writing some scripts.
    </p>

    <p>
      First of all, we want to know if we are already in tmux session so that we don&#8217;t try to jump into a session if we are already in one. This can be done easily by checking <code>$TMUX</code> environment variable, which tmux defines in tmux sessions.
    </p>

    <p>
      If we find we are not in a tmux session, we try to jump into one. Let&#8217;s create new session with <code>tmux new-session</code> command.
    </p>

    <p>
      By implementing these steps, whole script looks like this:
    </p>

    <p>
      <code data-gist-id='94cf8c9868f9bb95c923'></code>

      <p>
        Place it in the beginning of your <code>~/.zshrc</code> or <code>~/.bashrc</code> and you will have stronger relationship with tmux. If you want to use your shell outside of tmux frequently, remove <code>exit</code> command. This makes it possible to quit tmux session and continue using shell outside of tmux.
      </p>
    </p>
  </div></p>
</div>

<div id="outline-container-sec-2" class="outline-2">
  <h2 id="sec-2">
    What&#8217;s Next?
  </h2>

  <div class="outline-text-2" id="text-2">
    <p>
      This idea came from the book &#8220;<a href="http://pragprog.com/book/bhtmux/tmux" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://pragprog.com']);">tmux: Productive Mouse-Free Development</a>&#8220;. Before reading this book, I was thinking tmux is just a multiplexer. However, after reading this, I realized that the power of tmux lies in it&#8217;s scriptability and I came up with many ideas to improve my workflow. So, I suggest you to read it if you haven&#8217;t read it yet. It&#8217;s a quick read with 88 pages.
    </p></p>
  </div></p>
</div>
