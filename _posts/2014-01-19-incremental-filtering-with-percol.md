---
title: 'Making `| grep` Obsolete: Incremental Filtering with Percol'
layout: post
permalink: /incremental-filtering-with-percol/
dsq_thread_id:
  - 2143104016
categories:
  - Uncategorized
tags:
  - shell
---
<div id="outline-container-sec-1" class="outline-2">
  <h2 id="sec-1">
    What you get
  </h2>

  <div class="outline-text-2" id="text-1">
    <ul class="org-ul">
      <li>
        Faster, easier workflow of selecting lines from stdin
      </li>
      <li>
        Unlocked potential of making your shell life easier
      </li>
    </ul>
  </div></p>
</div>

<div id="outline-container-sec-2" class="outline-2">
  <h2 id="sec-2">
    What is percol?
  </h2>

  <div class="outline-text-2" id="text-2">
    <p>
      <a href="https://github.com/mooz/percol" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">Percol</a> gets input from a file or stdin, let you filter lines incrementally, and output selected lines to stdout. For vim users, it&#8217;s <a href="https://github.com/Shougo/unite.vim" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">unite.vim</a> for stdin. For emacs users, it&#8217;s <a href="http://emacs-helm.github.io/helm/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://emacs-helm.github.io']);">Emacs Helm</a> (previously anything.el) for stdin. For zsh users, it&#8217;s <a href="https://github.com/zsh-users/zaw" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">zaw</a> for stdin. For shell lovers, it&#8217;s incremental <code>| grep</code>. For others, watch this:
    </p>

    <p>
      <p>
        What&#8217;s great about percol is that it interacts with stdio, so it&#8217;s easy to combine percol with other programs to accomplish many tasks.
      </p>
    </p>
  </div></p>
</div>

<div id="outline-container-sec-3" class="outline-2">
  <h2 id="sec-3">
    Setup
  </h2>

  <div class="outline-text-2" id="text-3">
    <p>
      You can install percol using pip: <code>pip install percol</code>.
    </p>

    <p>
      I recommend you to take a look at <a href="https://github.com/mooz/percol#configuration" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">percol README configuration section</a>. But if you are busy, just make <code>~/.percol.d/rc.py</code> and write this to get nice keymaps:
    </p>

    <p>
      <code data-gist-id='8501936'></code> </div>
    </p>
  </div>

  <div id="outline-container-sec-4" class="outline-2">
    <h2 id="sec-4">
      Examples
    </h2>

    <div class="outline-text-2" id="text-4">
      <p>
        If you are using zsh, this zsh history search is the must:
      </p>

      <p>
        <code data-gist-id='8501974'></code> </div>
      </p>
    </div>

    <div id="outline-container-sec-5" class="outline-2">
      <h2 id="sec-5">
        What&#8217;s next?
      </h2>

      <div class="outline-text-2" id="text-5">
        <p>
          Sky is the limit! You can make many tasks easier. When you use <code>| grep</code> in interactive shell, maybe you can replace it with percol.
        </p>

        <p>
          Here are some more examples to spark your creativity: you can instantly checkout on your desired git branch (<code>alias gbs="git branch | percol | xargs git checkout"​</code>), or you can use percol to <a href="https://github.com/Genki-S/dotfiles/blob/master/zshfiles/rcfiles/percol.zsh#L11-L30" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">select clipboard history</a> (you need Mac and <a href="http://www.clipmenu.com/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://www.clipmenu.com']);">ClipMenu</a>).
        </p></p>
      </div></p>
    </div>
