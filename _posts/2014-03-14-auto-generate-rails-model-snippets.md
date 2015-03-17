---
title: Automatically Generate Snippet Definitions of Rails Models
layout: post
permalink: /auto-generate-rails-model-snippets/
dsq_thread_id:
  - 2435224425
categories:
  - Uncategorized
tags:
  - productivity
  - rails
---
Snippet (a.k.a. text expansion) is a great tool to boost your productivity. By using it, you not only type less and write more, but also reduce typos and syntax errors. So, you want to use snippets as much as possible.

However, there is one catch. You have to write snippet definitions. This can be tedious if you have many snippets you want to define.

I recently tried to make snippet definitions of all Rails models. Because my project has many models, I could not help automating it. Here&#8217;s how.

<div id="outline-container-sec-1" class="outline-2">
  <h2 id="sec-1">
    What You Get
  </h2>

  <div class="outline-text-2" id="text-1">
    <ul class="org-ul">
      <li>
        A script which generates snippet definitions of Rails models
      </li>
    </ul>
  </div></p>
</div>

<div id="outline-container-sec-2" class="outline-2">
  <h2 id="sec-2">
    Auto Generation. Easy and Consistent.
  </h2>

  <div class="outline-text-2" id="text-2">
    <p>
      The great thing about auto generation is that I don&#8217;t have to remember snippet triggers individually. I need a rule to auto generate, so I just have to remember the rule to use generated snippets. This time, I used the following rules:
    </p>

    <ol class="org-ol">
      <li>
        A Rails model is consist of namespaces and a model name (e.g. <code>NameSpace::RailsModel</code>)
      </li>
      <li>
        &#8216;::&#8217; is replaced with &#8216;:&#8217; (<code>NameSpace:RailsModel</code>)
      </li>
      <li>
        Collect uppercase letters and &#8216;:&#8217; (<code>NS:RM</code>)
      </li>
      <li>
        Make them lowercase, and it is the trigger of the snippet for the Rails model (<code>ns:rm</code> expands to <code>NameSpace::RailsModel</code>)
      </li>
      <li>
        Add &#8220;_&#8221; to the trigger, it will be the trigger for the Rails model in snake case (<code>ns:rm_</code> expands to <code>name_space_rails_model</code>)
      </li>
      <li>
        Each namespace and model name has it&#8217;s own snippet definitions (<code>ns</code> expands to <code>NameSpace</code>, <code>ns_</code> to <code>name_space</code>, <code>rm</code> to <code>RailsModel</code>, and <code>rm_</code> to <code>rails_model</code>)
      </li>
      <li>
        Optionally, it is possible to set prefix and suffix for snippet triggers to avoid collisions with other snippets (e.g. <code>ns;</code> rather than <code>ns</code>)
      </li>
    </ol>

    <p>
      So, if you know a model&#8217;s name, you can easily derive the snippet trigger.
    </p>

    <p>
      Here is the script I wrote to generate snippet definitions which follow above rule:
    </p>

    <p>
      <code data-gist-id='9557643'></code>

      <p>
        You might want to change snippet definition format (I use <a href="https://github.com/Shougo/neosnippet.vim" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">neosnippet</a>) and run options (I append &#8216;;&#8217; as suffix). Here is how to use it:
      </p>

      <pre class="example">
(from Rails root)
$ rails runner script/snippet_generator.rb &gt; snippets.snip
</pre>

      <p>
        I tried it for <a href="http://www.redmine.org/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://www.redmine.org']);">Redmine</a> project, and got following snippet definitions for the model <code>Repository::Bazaar</code>:
      </p>

      <p>
        <code data-gist-id='9557672'></code>

        <p>
          Snippet for <code>Bazaar</code> is not generated because there is a model with the same trigger <code>b;</code> and <code>b_;</code> previously.
        </p>
      </p></div>
    </p>
  </div>

  <div id="outline-container-sec-3" class="outline-2">
    <h2 id="sec-3">
      Where to place snippet definitions
    </h2>

    <div class="outline-text-2" id="text-3">
      <p>
        Now you have snippet definitions, but where you should place it? Because those are project specific snippet definitions, you don&#8217;t want to place those among global snippet definitions. If you are using vim, I recommend you to use a plugin which enable you to use project local vimrc (I name it as <code>.vimrc.local</code>). I am using <a href="https://github.com/MarcWeber/vim-addon-local-vimrc" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">vim-addon-local-vimrc</a>, and load local snippet definitions file from <code>.vimrc.local</code> (if you are using neosnippet, it&#8217;s <code>:NeoSnippetSource</code>). It looks like this:
      </p>

      <p>
        <code data-gist-id='9557764'></code>

        <p>
          If you don&#8217;t want the snippet definition file to pollute your <code>git status</code>, <a href="http://genkisugimoto.com/blog/keep-clean-git-working-tree/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://genkisugimoto.com']);">you can exclude it</a>.
        </p>
      </p>
    </div></p>
  </div>

  <div id="outline-container-sec-4" class="outline-2">
    <h2 id="sec-4">
      What&#8217;s next?
    </h2>

    <div class="outline-text-2" id="text-4">
      <p>
        I highly recommend you to try community driven snippet definitions (<a href="https://github.com/honza/vim-snippets" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">here</a> is for vim). By using it, you don&#8217;t have to define common snippets yourself (e.g. snippet for if-then-else statement). One catch is that you have to remember the trigger &#x2013; but I made it possible to search snippet definitions on the fly. I&#8217;ll cover it in the future post.
      </p></p>
    </div></p>
  </div>
