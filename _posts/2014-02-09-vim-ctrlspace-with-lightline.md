---
title: How to Use vim-ctrlspace with lightline.vim
layout: post
permalink: /vim-ctrlspace-with-lightline/
dsq_thread_id:
  - 2240097959
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
        Proper vim-ctrlspace statusline with lightline.vim
      </li>
      <li>
        Clean way to use <code>autocmd</code>
      </li>
    </ul>
  </div></p>
</div>

<div id="outline-container-sec-2" class="outline-2">
  <h2 id="sec-2">
    Manage your workspace with vim-ctrlspace
  </h2>

  <div class="outline-text-2" id="text-2">
    <p>
      A while ago, I found <a href="https://github.com/szw/vim-ctrlspace" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">vim-ctrlspace</a>, the vim workspace manager, and fell in love instantly after watching <a href="https://www.youtube.com/watchv%3D09l92uwKupI" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://www.youtube.com']);">this demo video</a>. I usually use <a href="https://github.com/Shougo/unite.vim" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">unite.vim</a> to search and open files, but managing workspace seemed to be a great productivity boost when dealing with complicated projects.
    </p>

    <p>
      When I tried it first, I thought vim-ctrlspace was a little sluggish and I had not developed the habit of using it. However, when I used it yesterday (while competing in <a href="http://www.staticshowdown.com/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://www.staticshowdown.com']);">Static Showdown</a>), I did not feel any sluggishness and it helped me a lot. One pitfall is that vim-ctrlspace uses statusline, so if you are using a statusline plugin (like <a href="https://github.com/Lokaltog/vim-powerline" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">vim-powerline</a>, <a href="https://github.com/bling/vim-airline" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">vim-airline</a> or <a href="https://github.com/itchyny/lightline.vim" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">lightline.vim</a>), you have to tweak your <code>vimrc</code> a little to see proper vim-ctrlspace statusline.
    </p>

    <p>
      I like lightline.vim because it is well designed and, as you guessed, light. I managed to use vim-ctrlspace along with lightline.vim, and I will write how.
    </p></p>
  </div></p>
</div>

<div id="outline-container-sec-3" class="outline-2">
  <h2 id="sec-3">
    Disable lightline.vim in vim-ctrlspace window
  </h2>

  <div class="outline-text-2" id="text-3">
    <p>
      vim-ctrlspace provides APIs to use in lightline.vim. I remember I tried that, but I didn&#8217;t quite get it work. I think disabling lightline.vim in vim-ctrlspace window is more straightforward and sustainable approach.
    </p>

    <p>
      This is possible because, as I noted above, lightline.vim is well designed. It uses <code>autocmd</code> to update statusline like this:
    </p>

    <p>
      <code data-gist-id='8891811'></code>

      <p>
        And it uses <code>augroup</code> well, so we can easily override those <code>autocmd</code>.
      </p><aside>

      <p>
        <code>augroup</code> is used to open a &#8220;scope&#8221; of <code>autocmd</code>. And <code>autocmd!</code> is used to delete existing <code>autocmd</code> &#8220;in the current scope&#8221;. So, you can delete all <code>autocmd</code> in <code>LightLine</code> group by issuing <code>autocmd!</code> in <code>LightLine</code> scope like this:
      </p>

      <p>
        <code data-gist-id='8891894'></code> </aside>

        <p>
          Now let&#8217;s disable lightline.vim only in vim-ctrlspace window. It is as simple as writing a filter function which execute normal lightline.vim operation except for vim-ctrlspace window. Because vim-ctrlspace window sets its <code>bufname</code> as <code>​"__CS__"​</code>, we can stop lightline.vim execution when <code>bufname('%')</code> equals to <code>​"__CS__"​</code>. The function looks like this:
        </p>

        <p>
          <code data-gist-id='8891969'></code>

          <p>
            And finally, we can define our self <code>autocmd</code> to call this filter function like this:
          </p>

          <p>
            <code data-gist-id='8892016'></code> </div>
          </p></div>

          <div id="outline-container-sec-4" class="outline-2">
            <h2 id="sec-4">
              What&#8217;s Next?
            </h2>

            <div class="outline-text-2" id="text-4">
              <p>
                Now you can use vim-ctrlspce with it&#8217;s proper statusline, it&#8217;s time to master vim-ctrlspace workflow. I am learning it now and it was difficult at first, but after I remembered a few basic operations, it became super useful. The saving and loading of workspace work quite well, it&#8217;s far better than the <code>:mksession</code> feature of vim. It&#8217;s worth checking out just to use this feature.
              </p></p>
            </div></p>
          </div>
