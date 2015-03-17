---
title: How to Lazy Load Vim Plugins
layout: post
permalink: /how-to-lazy-load-vim-plugins/
dsq_thread_id:
  - 2120324063
categories:
  - Uncategorized
tags:
  - vim
---
<div id="outline-container-sec-1" class="outline-2">
  <h2 id="sec-1">
    What You Get
  </h2>

  <div class="outline-text-2" id="text-1">
    <ul class="org-ul">
      <li>
        Vim with faster startup time
      </li>
    </ul>
  </div></p>
</div>

<div id="outline-container-sec-2" class="outline-2">
  <h2 id="sec-2">
    What is NeoBundle
  </h2>

  <div class="outline-text-2" id="text-2">
    <p>
      <a href="https://github.com/Shougo/neobundle.vim" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">NeoBundle</a> is a plugin manager for vim. It makes installing/updating/cleaning vim plugins easy.
    </p>

    <p>
      There is a similar plugin named <a href="https://github.com/gmarik/vundle" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">Vundle</a> (actually, NeoBundle was originally a fork of it). NeoBundle has many advantages over Vundle, and one of those is lazy loading, which is essential to keep vim&#8217;s startup time bearable when using many plugins.
    </p>

    <p>
      NeoBundle is written by Shougo, a Japanese programmer. So, while there are many Japanese articles about NeoBundle, I could not find any article in English. That&#8217;s why I decided to write this article. Note that the document of NeoBundle is well written in English. So you can always see <code>:h neobundle</code> to get detailed help.
    </p><aside>

    <p>
      Shougo is one of the most famous Japanese vim user, who is really passionate about vim. His plugins are high in quality, and so well maintained that Japanese vim users admire his software by calling it &#8220;ShougoWare&#8221;. I regard him as one of my vim heroes, along with (of course) tpope, kana, etc.
    </p></aside>
  </div></p>
</div>

<div id="outline-container-sec-3" class="outline-2">
  <h2 id="sec-3">
    Basic usage
  </h2>

  <div class="outline-text-2" id="text-3">
    <p>
      I recommend you to see the quick start on <a href="https://github.com/Shougo/neobundle.vim" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">NeoBundle README</a>. Apart from required snippets you have to copy & paste, using it is quite simple. After setup, if you want to install a plugin from github repository, just write <code>NeoBundle "github-user/repository"​</code> in your .vimrc and issue <code>:NeoBundleInstall</code>, and you have it.
    </p></p>
  </div></p>
</div>

<div id="outline-container-sec-4" class="outline-2">
  <h2 id="sec-4">
    How to Lazy Load
  </h2>

  <div class="outline-text-2" id="text-4">
    <p>
      If you use <code>NeoBundle "user/repo"​</code> in your .vimrc, the plugin is loaded at the startup. There are 2 ways to tell NeoBundle not to load plugins at the startup.
    </p>

    <p>
      <code data-gist-id='8415526'></code>

      <p>
        I prefer latter because it is much easier to toggle lazy option (you can just delete &#8216;lazy&#8217; line).
      </p>

      <p>
        You can issue &#8220;NeoBundleSource repo&#8221; to source the plugin manually. Or you can add triggers to source it. There are many triggers you can use (see <code>:h *neobundle-options-autoload*</code>). I think these are particularly useful:
      </p>

      <dl class="org-dl">
        <dt>
          filetypes
        </dt>

        <dd>
          when filetype is set to one of the specified types
        </dd>

        <dt>
          commands
        </dt>

        <dd>
          when one of the specified commands is issued
        </dd>

        <dt>
          mappings
        </dt>

        <dd>
          when one of the specified mappings is triggered
        </dd>
      </dl>

      <p>
        Example:
      </p>

      <p>
        <code data-gist-id='8415549'></code>

        <p>
          In this case, the plugin is loaded when one of these events are occurred:
        </p>

        <ul class="org-ul">
          <li>
            filetype is set to &#8216;vim&#8217; or &#8216;elisp&#8217;
          </li>
          <li>
            <code>:Command</code> is issued
          </li>
          <li>
            <code>&lt;Plug&gt;(plugin_mapping)</code> is triggered
          </li>
        </ul></div>
      </p></div>

      <div id="outline-container-sec-5" class="outline-2">
        <h2 id="sec-5">
          What&#8217;s next?
        </h2>

        <div class="outline-text-2" id="text-5">
          <p>
            You might want to manage vim plugins via yaml file <a href="https://github.com/Genki-S/dotfiles/blob/master/vimfiles/vim/bundles.yml" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">like me</a>. Because it&#8217;s beautiful and easy to change options than editing vimscript (I hate newline & backslash syntax). I am planning to write about it in my future post.
          </p></p>
        </div></p>
      </div>
