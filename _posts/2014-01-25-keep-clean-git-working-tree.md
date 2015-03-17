---
title: How to Force Yourself to Keep Clean Git Working Tree
layout: post
permalink: /keep-clean-git-working-tree/
dsq_thread_id:
  - 2174677880
categories:
  - Uncategorized
tags:
  - git
---
<div id="outline-container-sec-1" class="outline-2">
  <h2 id="sec-1">
    What you get
  </h2>

  <div class="outline-text-2" id="text-1">
    <ul class="org-ul">
      <li>
        No more pushing without adding necessary files
      </li>
      <li>
        Cleaner <code>git status</code> output <img src="http://genkisugimoto.com/blog/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" />
      </li>
    </ul>
  </div></p>
</div>

<div id="outline-container-sec-2" class="outline-2">
  <h2 id="sec-2">
    Background
  </h2>

  <div class="outline-text-2" id="text-2">
    <p>
      I am really lazy and my git repositories tend to be messy. I sometimes write useful scripts but I don&#8217;t commit it nor remove it from project directories. So, my <code>git status</code> tends to output a lot of &#8220;untracked&#8221; files.
    </p>

    <p>
      One day, I pushed commits without adding necessary files. This caused some time loss on my team. I hate wasting time, regardless of mine or of others. So I determined to keep my git repositories clean to prevent this from happening again.
    </p></p>
  </div></p>
</div>

<div id="outline-container-sec-3" class="outline-2">
  <h2 id="sec-3">
    Using git pre-push hook
  </h2>

  <div class="outline-text-2" id="text-3">
    <p>
      I wrote a git pre-push hook which prevents me from pushing when my repository is dirty. This way, I cannot push commits if any untracked files exist, and I will not likely to push flawed commits again. You can use this too by saving the script below as <code>.git/hooks/pre-push</code> in your repositories (make sure you make it executable).
    </p>

    <p>
      <code data-gist-id='8623216'></code> </div>
    </p>
  </div>

  <div id="outline-container-sec-4" class="outline-2">
    <h2 id="sec-4">
      Oasis named &#8220;trash&#8221;
    </h2>

    <div class="outline-text-2" id="text-4">
      <p>
        However, I still sometimes want to keep temporary files in my repository, but don&#8217;t want to commit those. To manage this situation, I found <code>.git/info/exclude</code> file useful. It is <code>.gitignore</code> you don&#8217;t have to commit. So, you can ignore files only in your repositories.
      </p>

      <p>
        I made a directory named &#8220;stash&#8221; in my repository and ran <code>echo 'stash' &gt;&gt; .git/info/exclude</code>. Now I can keep my crappy scripts in the &#8220;stash&#8221; directory without being committed nor being listed as &#8220;untracked&#8221;.
      </p></p>
    </div></p>
  </div>

  <div id="outline-container-sec-5" class="outline-2">
    <h2 id="sec-5">
      What&#8217;s Next?
    </h2>

    <div class="outline-text-2" id="text-5">
      <p>
        If you think you will use <code>.git/info/exclude</code> a lot, following script might be useful. After saving it as &#8220;git-exclude&#8221; and making it executable, you can issue <code>git exclude 'file'​</code> to add files to <code>.git/info/exclude</code>.
      </p>

      <p>
        <code data-gist-id='8623241'></code>

        <p>
          You might want to manage git hooks the nicer way if you want to use multiple hooks. I found <a href="https://github.com/icefox/git-hooks" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">icefox/git-hooks</a> and it seems promising. The great thing about it is that it allows me to have &#8220;User hooks&#8221; in <code>~/.git_hooks</code>. So, now I can manage my git hooks effortlessly in my dotfiles repository.
        </p>
      </p>
    </div></p>
  </div>
