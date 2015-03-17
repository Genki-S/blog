---
title: How to Prevent Committing Undesired Files
layout: post
permalink: /how-to-prevent-committing-undesired-files/
dsq_thread_id:
  - 2488371872
categories:
  - Uncategorized
tags:
  - git
---
Bulk staging commands like `git add .` are useful, but it can cause the trouble of staging undesired files. One example is adding `*.orig` files which are generated when you use mergetool. Recently, <a href="https://github.com/Genki-S/dotfiles/commit/db920f589c7225a8312927fcf0fe123daf309785" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">I did it</a>. So I built a system which prevents me from doing it again. Here is how.

<div id="outline-container-sec-1" class="outline-2">
  <h2 id="sec-1">
    What You Get
  </h2>

  <div class="outline-text-2" id="text-1">
    <ul class="org-ul">
      <li>
        A git pre-commit hook which prevents you from committing files matching certain patterns
      </li>
    </ul>
  </div></p>
</div>

<div id="outline-container-sec-2" class="outline-2">
  <h2 id="sec-2">
    You can just ignore, I prefer to check
  </h2>

  <div class="outline-text-2" id="text-2">
    <p>
      One easy solution would be to add <code>*.orig</code> to your <code>.gitignore</code>. However, I&#8217;m sure I would not notice generated <code>*.orig</code> files if <code>git status</code> does not show them. So, I chose to use pre-commit hook so that I can still notice <code>*.orig</code> files.
    </p></p>
  </div></p>
</div>

<div id="outline-container-sec-3" class="outline-2">
  <h2 id="sec-3">
    The Script
  </h2>

  <div class="outline-text-2" id="text-3">
    <p>
      Here is the script to check if <code>*.orig</code> files are included in files to be committed:
    </p>

    <p>
      <code data-gist-id='9718868'></code>

      <p>
        This script is designed to use with <a href="https://github.com/icefox/git-hooks" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">git-hooks</a>, but you can paste the contents of <code>run_test</code> function in your normal <code>.git/hooks/pre-commit</code> file as well.
      </p>
    </p>
  </div></p>
</div>

<div id="outline-container-sec-4" class="outline-2">
  <h2 id="sec-4">
    What&#8217;s Next?
  </h2>

  <div class="outline-text-2" id="text-4">
    <p>
      To be honest, I am not sure if this script was worth the effort because I have never reaped a benefit from those <code>*.orig</code> files. I found that <a href="http://stackoverflow.com/questions/1251681/diff-tool-generates-unwanted-orig-files" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://stackoverflow.com']);">it is possible to make mergetool not generate those <code>*.orig</code> files</a> (<code>git config --global mergetool.keepBackup false</code>). It might be a better approach because I don&#8217;t have to <code>git clean</code> (or <code>rm **/*.orig</code>) after using mergetool.
    </p>

    <p>
      Anyway, it&#8217;s great to be able to prevent committing in certain conditions using pre-commit hook. For example, it might be used to prevent you from committing files with, say, hard coded breakpoints like <code>binding.pry</code> in ruby.
    </p></p>
  </div></p>
</div>
