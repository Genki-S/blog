---
title: Vim Plugin Settings Made Easy and Beautiful
layout: post
permalink: /vim-plugin-settings-made-easy-and-beautiful/
dsq_thread_id:
  - 2305765375
categories:
  - Uncategorized
tags:
  - vim
---
If you use many vim plugins, where to place the plugin settings is one of the most difficult problem. In order to be a better vim user, you have to <a href="http://learnvimscriptthehardway.stevelosh.com/chapters/07.html" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://learnvimscriptthehardway.stevelosh.com']);">make it effortless to edit your <code>.vimrc</code> </a>. The same thing applies for plugin settings. In order to edit vim plugin settings as effortlessly as possible, I implemented a system which satisfies these requirements:

<ul class="org-ul">
  <li>
    I can start editing plugin settings right away
  </li>
  <li>
    I don&#8217;t have to make efforts to keep the rules of the system
  </li>
</ul>

Here&#8217;s how.

<div id="outline-container-sec-1" class="outline-2">
  <h2 id="sec-1">
    Existing Approaches, and Why They Don&#8217;t Work
  </h2>

  <div class="outline-text-2" id="text-1">
    <p>
      First of all, let&#8217;s see why existing approaches didn&#8217;t satisfy my needs. I think there are 2 major approaches.
    </p>

    <p>
      One is to put all plugin settings in <code>.vimrc</code> file. Even though opening the <code>.vimrc</code> might be fast, you have to search where you placed the settings of that particular plugin you want to edit. And if you use many plugins, your <code>.vimrc</code> becomes huge and I think it&#8217;s difficult to edit.
    </p>

    <p>
      Another approach is to <a href="https://github.com/skwp/dotfiles/tree/master/vim/settings" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">split files</a> and <a href="https://github.com/skwp/dotfiles/blob/master/vim/settings.vim" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">source them all</a> like <a href="https://github.com/skwp/dotfiles" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">YADR</a>. Because it manages settings by files named <code>{plugin-name}.vim</code>, you know where the settings of a plugin lies. However, by splitting files, it becomes tougher to find and open a file you want to edit. And you have to make some efforts to keep the name of plugin setting files consistent.
    </p></p>
  </div></p>
</div>

<div id="outline-container-sec-2" class="outline-2">
  <h2 id="sec-2">
    Using Plugin Manager
  </h2>

  <div class="outline-text-2" id="text-2">
    <p>
      I thought the second approach was almost satisfying my needs.
    </p>

    <p>
      If I were able to find setting files more quickly. If I didn&#8217;t have to remember to keep file names consistent.
    </p>

    <p>
      I noticed that I could satisfy these by completion of plugin names. If I can use completion when I open a plugin setting file, I can find it more quickly. And I don&#8217;t have to check correct plugin names when I want to add new setting files.
    </p>

    <p>
      So, I created this <code>:EditPluginSetting</code> command:
    </p>

    <p>
      <code data-gist-id='9165361'></code>

      <p>
        When I want to edit plugin settings, I just issue <code>:EditPluginSetting</code> command and hit <code>&lt;Tab&gt;</code> to let <a href="https://github.com/Shougo/neobundle.vim" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">NeoBundle</a>, the plugin manager, complete plugin names for me. For example, when I want to edit a plugin which is related to Ruby on Rails, I can type <code>:EditPluginSetting rails</code> and hit <code>&lt;Tab&gt;</code>, then the plugins which has &#8220;rails&#8221; in the name are shown like this:
      </p><figure>

      <p>
        <img src="http://genkisugimoto.com/blog/wp-content/uploads/2014/02/wpid-plugin-name-completion1.png" alt="plugin-name-completion.png" />
      </p><figcaption>

      <span class="figure-number">Figure 1:</span> plugin name completion</figcaption> </figure>

      <p>
        If there is one match, it completes the matching plugin name. So it is quick to access plugin setting files and I don&#8217;t have to remember plugin names exactly.
      </p>

      <p>
        When you hit <code>&lt;CR&gt;</code>, it opens <code>{plugin-name}.vim</code> file under the directory specified by <code>s:plugin_setting_dirname</code>. You want the directory be under version control.
      </p>

      <p>
        By using <a href="https://github.com/tyru/vim-altercmd" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">vim-altercmd</a>, I can issue <code>ps</code> command instead of <code>EditPluginSetting</code>, and it makes editing plugin settings blazing fast.
      </p>
    </p>
  </div></p>
</div>

<div id="outline-container-sec-3" class="outline-2">
  <h2 id="sec-3">
    What&#8217;s Next?
  </h2>

  <div class="outline-text-2" id="text-3">
    <p>
      As I <a href="http://genkisugimoto.com/blog/how-to-lazy-load-vim-plugins/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://genkisugimoto.com']);">wrote before</a>, vim plugins can be loaded lazily. Then, what&#8217;s the point of loading settings of lazy plugins on vim startup? I <a href="https://github.com/Genki-S/dotfiles/blob/master/vimfiles/vim/neobundle.vim" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">implemented a method</a> to load plugin settings lazily as well as plugins themselves. I will cover this in the future.
    </p></p>
  </div></p>
</div>
