---
title: Manage Vim Plugins the Beautiful Way using Yaml
layout: post
permalink: /manage-vim-plugins-via-yaml/
dsq_thread_id:
  - 2232340267
categories:
  - Uncategorized
tags:
  - vim
---
<div id="outline-container-sec-1" class="outline-2">
  <h2 id="sec-1">
    What you get
  </h2>

  <div class="outline-text-2" id="text-1">
    <ul class="org-ul">
      <li>
        <a href="https://github.com/Genki-S/dotfiles/blob/master/vimfiles/vim/bundles.yml" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">Beautiful list</a> of vim plugins
      </li>
    </ul>
  </div></p>
</div>

<div id="outline-container-sec-2" class="outline-2">
  <h2 id="sec-2">
    Prerequisite
  </h2>

  <div class="outline-text-2" id="text-2">
    <ul class="org-ul">
      <li>
        Using <a href="https://github.com/Shougo/neobundle.vim" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">NeoBundle</a> (I think it works with <a href="https://github.com/gmarik/vundle" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">Vundle</a> as well)
      </li>
    </ul>
  </div></p>
</div>

<div id="outline-container-sec-3" class="outline-2">
  <h2 id="sec-3">
    Vimscript is not so beautiful
  </h2>

  <div class="outline-text-2" id="text-3">
    <p>
      When you are using NeoBundle and passing many options for plugins, your vimrc might look like this:
    </p>

    <p>
      <code data-gist-id='8834329'></code>

      <p>
        I&#8217;m not a fan of vimscript&#8217;s newline & backslash syntax, which you use to break a line in the middle of a command. I&#8217;m not sure how I should indent it (my autoindent setting is not so smart at this problem&#x2026;). And things get crazy when you want to join a multiline command into one line. So, I don&#8217;t want to use multiline commands where I am sure I change a lot, and vim plugin list and options are one of those.
      </p>
    </p>
  </div></p>
</div>

<div id="outline-container-sec-4" class="outline-2">
  <h2 id="sec-4">
    Meet yaml
  </h2>

  <div class="outline-text-2" id="text-4">
    <p>
      I found it best to use yaml to manage my vim plugins and options because NeoBundle command takes repository name as the first argument and options dictionary as the second argument. You can build yaml file with the following structure:
    </p>

    <p>
      <code data-gist-id='8834752'></code>

      <p>
        And then, you can parse it and store into a variable. You can use any parser, I use one from ruby like this:
      </p>

      <p>
        <code data-gist-id='8834793'></code>

        <p>
          It does following (note that &#8220;hash&#8221; is for ruby and &#8220;dictionary&#8221; is for vim):
        </p>

        <ul class="org-ul">
          <li>
            Invoke ruby
          </li>
          <li>
            Load yaml file (which turns into a hash)
          </li>
          <li>
            Generate string representation of the hash
          </li>
          <li>
            Modify the string into the form of vim dictionary&#8217;s string representation
          </li>
          <li>
            Let vim (from within ruby) evaluate the string and store the dictionary into vim&#8217;s local variable
          </li>
        </ul><aside>

        <p>
          You need to compile vim with ruby support to use ruby from within vim. You can check if your vim has ruby support by the command <code>vim --version | grep ruby</code>. If it outputs <code>-ruby</code>, then you don&#8217;t have ruby support. If it outputs <code>+ruby</code>, then you have it.
        </p>

        <p>
          I know some minimalist does not like my method because not all vim have ruby support. But I&#8217;m happy with it because I&#8217;m not likely to use vim without ruby support.
        </p></aside></div>
      </p></div>

      <div id="outline-container-sec-5" class="outline-2">
        <h2 id="sec-5">
          Loop plugins and let NeoBundle manage it
        </h2>

        <div class="outline-text-2" id="text-5">
          <p>
            Now that we have our plugin list in a variable, we can loop it and invoke <code>NeoBundle</code> command like this:
          </p>

          <p>
            <code data-gist-id='8835962'></code>

            <p>
              I love the beauty of writing <code>NeoBundle</code> command only once.
            </p>
          </p>
        </div></p>
      </div>

      <div id="outline-container-sec-6" class="outline-2">
        <h2 id="sec-6">
          What&#8217;s Next?
        </h2>

        <div class="outline-text-2" id="text-6">
          <p>
            We are now able to manage vim plugins quite easily by modifing yaml file. If you install vim plugins frequently, I recommend you to use <a href="https://github.com/AndrewRadev/switch.vim" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">switch.vim</a> to make installing process lightning fast. It allows you to predefine substitution patterns and invoke it when the cursor is one of the predefined patterns (i.e. it&#8217;s predefined <code>:s</code> command).
          </p>

          <p>
            Put the following to your vimrc:
          </p>

          <p>
            <code data-gist-id='8839254'></code>

            <p>
              Using this setting, you can copy and paste a vim plugin&#8217;s github url and substitute it to proper yaml format instantly.
            </p>

            <p>
              Now there are no obstacles to try out many plugins. However, be careful not to overload your vim with too many plugins (like me), it makes your vim slow. You can cope with this problem with NeoBundle&#8217;s lazy loading feature, which I covered <a href="http://genkisugimoto.com/blog/how-to-lazy-load-vim-plugins/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://genkisugimoto.com']);">here</a>.
            </p>

            <p>
              By the way, switch.vim is so awesome that I recommend you to use it for many purposes other than this as well.
            </p>
          </p>
        </div></p>
      </div>
