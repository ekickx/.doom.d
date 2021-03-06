
# Table of Contents

-   [New Changes](#org66a0072)
    -   [<span class="timestamp-wrapper"><span class="timestamp">[2020-09-25 Fri]</span></span>](#org6cbfa0c)
    -   [<span class="timestamp-wrapper"><span class="timestamp">[2020-08-26 Wed]</span></span>](#org815f3d2)
    -   [<span class="timestamp-wrapper"><span class="timestamp">[2020-07-22 Wed]</span></span>](#org1d791c1)
    -   [<span class="timestamp-wrapper"><span class="timestamp">[2020-06-21 Sun]</span></span>](#orgfb48df5)
    -   [<span class="timestamp-wrapper"><span class="timestamp">[2020-06-02 Tue]</span></span>](#orgc0b58cf)
-   [Requirements](#orgbe98998)
-   [Default Settings](#org7f551ec)
-   [User Information](#org54f50bb)
-   [Misc Settings](#orgc29e828)
-   [Key Bindings](#orgab8a672)
-   [Terminal Mode](#orgd57531b)
-   [Default folder(s) and file(s)](#org4404d8b)
-   [Setup Layout by Monitor Profile](#org6defe56)
-   [Org mode settings](#org37f572b)
    -   [Capture Templates](#orga250cb7)
-   [Directory settings](#orgbdfb10f)
-   [Export Settings](#org17a60fd)
-   [Misc Org Mode settings](#org20050c4)
-   [Keywords](#orgaa31f79)
-   [Logging and Drawers](#org4796c58)
-   [Properties](#orgcbb41bf)
-   [Publishing](#org47c61f2)
-   [Refiling Defaults](#org802da9b)
-   [Orgmode Startup](#orgeb565f8)
-   [Org Protocol](#org6d856da)
-   [Default Tags](#org0c387b0)
-   [Buffer Settings](#org4b5cbf7)
-   [Misc Settings](#org850df91)
-   [Module Settings](#org8a23669)
    -   [company mode](#org53a3414)
    -   [Define Word](#org3b58d36)
    -   [Misc Modules [Bookmarks, PDF Tools]](#orgac578cc)
    -   [Graphs and Chart Modules](#org0820dd7)
    -   [Elfeed](#orgee09d4b)
    -   [DEFT](#org9a25b46)
    -   [Org-Rifle](#org73671ab)
    -   [Pandoc](#org528fa08)
    -   [ROAM](#org4538107)
    -   [ROAM Server](#org13b4324)
    -   [ROAM Export Backlinks + Content](#org8244406)
    -   [Reveal [HTML Presentations]](#org87ff447)
    -   [Super Agenda Settings](#org0e97f81)
-   [Loading secrets](#org688147c)
-   [Hacks](#orge36968c)
-   [Custom Functions](#org3f809b2)
    -   [Time Stamps](#org72dc77c)
    -   [Capture Template File Picker](#org7959977)
    -   [Clarify Tasks](#orgd7c5bd4)
    -   [Capture headline finder](#org2948d1f)
    -   [Search file headlines and send tree to indirect buffer](#org2936ccd)
    -   [Change Font](#org64e390b)
-   [Theme Settings](#org9080b23)

![img](attachments/workspace.png)


<a id="org66a0072"></a>

# New Changes


<a id="org6cbfa0c"></a>

## <span class="timestamp-wrapper"><span class="timestamp">[2020-09-25 Fri]</span></span>

1.  Added new clarify function for task items.. You can define your property values to the variable `org-tasks-properties-metadata`, then call `nm/org-clarify-metadata` and it will PROMPT to update for tasks that are missing a value.
    1.  You can also define multiple lists, and pass the variable as an argument to `nm/org-clarify-task-properties`, as such `(nm/org-clarify-task-properties org-tasks-properties-lists2)`
2.  Added `nm/org-assign-tasks-proj` function to update task `org-todo-keyword` as PROJ when child-task exist and vice-versa. This function has been set as a `before-save-hook`.   
    ![img](attachments/proj-tasks-update.gif)


<a id="org815f3d2"></a>

## <span class="timestamp-wrapper"><span class="timestamp">[2020-08-26 Wed]</span></span>

1.  Moved `roam-db-directory` to **.emacs.d** directory FIXME address syncthing permission issue
2.  Added **FiraCode** fonts (see [Requirements](#orgbe98998))


<a id="org1d791c1"></a>

## <span class="timestamp-wrapper"><span class="timestamp">[2020-07-22 Wed]</span></span>

1.  Added new functions specifically for GTD workflow, this will require some changes to fit your needs:
2.  Moved GTD Module to <gtd.el>
3.  Configure your variable settings in Setting up my GTD Methodology


<a id="orgfb48df5"></a>

## <span class="timestamp-wrapper"><span class="timestamp">[2020-06-21 Sun]</span></span>

1.  metrics-tracker + capture-template for habit tracker (see ~/.doom.d/templates/habitstracker.org)
2.  new templates for captures, breakfix, meeting-notes, diary and more&#x2026; (check the ~/.doom.d/templates/.. directory)
3.  added org-roam-server


<a id="orgc0b58cf"></a>

## <span class="timestamp-wrapper"><span class="timestamp">[2020-06-02 Tue]</span></span>

1.  Added `org-roam`
2.  Added agenda schdules faces (thanks to )
3.  Search and narrow&#x2026; Bound to `SPC ^`, this provides a function to pick a headline from the current buffer and narrow to it.
4.  Agenda-Hook to narrow on current subtree
5.  Deft mode with custom title maker (thanks to [jingsi&rsquo;s space](https://jingsi.space/post/2017/04/05/organizing-a-complex-directory-for-emacs-org-mode-and-deft/))
6.  GTD Inbox Processing &#x2026; Credit to Jethro for his function. Function is bound to `jethro/org-inbox-process`
7.  [Org-Web-Tools](https://github.com/alphapapa/org-web-tools), thanks Alphapapa for the awesome package.


<a id="orgbe98998"></a>

# Requirements

These are some items that are required outside of the normal DOOM EMACS installation, before you can use this config. The idea here is to keep this minimum so as much of this is close to regular DOOM EMACS.

1.  **SQLITE3 Installation**: You will need to install sqlite3, typicalled installed via your package manager as `sudo apt install sqlite3`
2.  For fonts please download [Input](https://input.fontbureau.com/download/), [DejaVu](http://sourceforge.net/projects/dejavu/files/dejavu/2.37/dejavu-fonts-ttf-2.37.tar.bz2) and [FiraCode](https://github.com/tonsky/FiraCode)


<a id="org7f551ec"></a>

# Default Settings

In this section we are going to cover all the basics, and then tangle the results into `config.el`

    (setq initial-buffer-choice "~/.org/gtd/next.org")


<a id="org54f50bb"></a>

# User Information

Environment settings, which are specific to the user and system. First up are user settings.

    (setq user-full-name "Nick Martin"
          user-mail-address "nmartin84@gmail.com")


<a id="orgc29e828"></a>

# Misc Settings

Now we load some default settings for EMACS.

    (display-time-mode 1)
    (setq display-time-day-and-date t)


<a id="orgab8a672"></a>

# Key Bindings

From here we load some extra key bindings that I use often

    (bind-key "<f6>" #'link-hint-copy-link)
    (map! :after org
          :map org-mode-map
          :leader
          :desc "Move up window" "<up>" #'evil-window-up
          :desc "Move down window" "<down>" #'evil-window-down
          :desc "Move left window" "<left>" #'evil-window-left
          :desc "Move right window" "<right>" #'evil-window-right
          :prefix ("s" . "+search")
          :desc "Outline" "o" #'counsel-outline
          :desc "Counsel ripgrep" "d" #'counsel-rg
          :desc "Swiper All" "@" #'swiper-all
          :desc "Rifle Buffer" "b" #'helm-org-rifle-current-buffer
          :desc "Rifle Agenda Files" "a" #'helm-org-rifle-agenda-files
          :desc "Rifle Project Files" "#" #'helm-org-rifle-project-files
          :desc "Rifle Other Project(s)" "$" #'helm-org-rifle-other-files
          :prefix ("l" . "+links")
          "o" #'org-open-at-point
          "g" #'eos/org-add-ids-to-headlines-in-file)
    
    (map! :after org-agenda
          :map org-agenda-mode-map
          :localleader
          :desc "Filter" "f" #'org-agenda-filter)


<a id="orgd57531b"></a>

# Terminal Mode

Set a few settings if we detect terminal mode

    (when (equal (window-system) nil)
      (and
       (bind-key "C-<down>" #'+org/insert-item-below)
       (setq doom-theme 'doom-monokai-pro)
       (setq doom-font (font-spec :family "Input Mono" :size 20))))


<a id="org4404d8b"></a>

# Default folder(s) and file(s)

Then we will define some default files. I&rsquo;m probably going to use default task files for inbox/someday/todo at some point so expect this to change. Also note, all customer functions will start with a `+` to distinguish from major symbols.

    (setq diary-file "~/.org/diary.org")
    (setq org-directory "~/.org/")


<a id="org6defe56"></a>

# Setup Layout by Monitor Profile

    (when (equal system-type 'gnu/linux)
      (setq doom-font (font-spec :family "Fira Code" :size 18)
            doom-big-font (font-spec :family "Fira Code" :size 26)))
    (when (equal system-type 'windows-nt)
      (setq doom-font (font-spec :family "InputMono" :size 18)
            doom-big-font (font-spec :family "InputMono" :size 22)))
    
    ; TODO Re-write new function for popup profile setup.
    (after! org (set-popup-rule! "^\\*lsp-help" :side 'bottom :size .30 :select t)
      (set-popup-rule! "*helm*" :side 'right :size .30 :select t)
      (set-popup-rule! "*Org QL View:*" :side 'right :size .25 :select t)
      (set-popup-rule! "*Capture*" :side 'left :size .30 :select t)
      (set-popup-rule! "*CAPTURE-*" :side 'left :size .30 :select t)
      (set-popup-rule! "*Org Agenda*" :side 'right :size .35 :select t))


<a id="org37f572b"></a>

# Org mode settings

First I like to add some extra fancy stuff to make orgmode more appealing when i&rsquo;m using `+pretty` flag.

    (after! org (setq org-hide-emphasis-markers t
                      org-hide-leading-stars t
                      org-list-demote-modify-bullet '(("+" . "-") ("1." . "a.") ("-" . "+"))))
    ;                  org-ellipsis "▼"))

-   Other options for ellipsis &ldquo;▼, ↴, ⬎, ⤷,…, and ⋱.&rdquo;
-   Extra options for headline-bullets-list: &ldquo;◉&rdquo; &ldquo;●&rdquo; &ldquo;○&rdquo; &ldquo;∴&rdquo;

Add a when condition that only adjust settings when certain features are enabled&#x2026; This depends on where i&rsquo;m running Emacs from (eg: Terminla, X11 or native).

    (when (require 'org-superstar nil 'noerror)
      (setq org-superstar-headline-bullets-list '("◉" "●" "○")
            org-superstar-item-bullet-alist nil))

Adding additional search functions

    (defun zyro/rifle-roam ()
      "Rifle through your ROAM directory"
      (interactive)
      (helm-org-rifle-directories org-roam-directory))
    
    (map! :after org
          :map org-mode-map
          :leader
          :prefix ("n" . "notes")
          :desc "Rifle ROAM Notes" "!" #'zyro/rifle-roam)

Setting up my initial agenda settings

    (after! org (setq org-agenda-diary-file "~/.org/diary.org"
                      org-agenda-dim-blocked-tasks t
                      org-agenda-use-time-grid t
                      org-agenda-hide-tags-regexp "\\w+"
                      org-agenda-compact-blocks nil
                      org-agenda-block-separator ""
                      org-agenda-skip-scheduled-if-done t
                      org-agenda-skip-deadline-if-done t
                      org-agenda-window-setup 'current-window
                      org-enforce-todo-checkbox-dependencies nil
                      org-enforce-todo-dependencies t
                      org-habit-show-habits t))
    
    (after! org (setq org-agenda-files (append (file-expand-wildcards "~/.org/gtd/*.org"))))

Adjusting clock settings

    (after! org (setq org-clock-continuously t))


<a id="orga250cb7"></a>

## Capture Templates

Here we setup the capture templates we want for `org-capture`. I use a file template that&rsquo;s pre-filled with my monthly scheduled transactions. (TODO: Add default file-template for new projects.)

    (after! org (setq org-capture-templates
          '(("!" "Quick Capture" plain (file "~/.org/gtd/inbox.org")
             "* TODO %(read-string \"Task: \")\n:PROPERTIES:\n:CREATED: %U\n:END:")
            ("p" "New Project" plain (file nm/org-capture-file-picker)
             (file "~/.doom.d/templates/template-projects.org"))
            ("n" "Note on headline" plain (function nm/org-end-of-headline)
             "%?" :empty-lines-before 1 :empty-lines-after 1)
            ("q" "quick note to file" entry (function nm/org-capture-weeklies)
             "* %?" :empty-lines-before 1 :empty-lines-after 1)
            ("$" "Scheduled Transactions" plain (file "~/.org/gtd/finances.ledger")
             (file "~/.doom.d/templates/ledger-scheduled.org"))
            ("l" "Ledger Transaction" plain (file "~/.org/gtd/finances.ledger")
             "%(format-time-string \"%Y/%m/%d\") * %^{transaction}\n Income:%^{From Account|Checking|Card|Cash}  -%^{dollar amount}\n Expenses:%^{category}  %\\3\n" :empty-lines-before 1))))

Example ledger template file: = `/.doom.d/templates/ledger-scheduled.org`

    %(format-time-string "%Y/%m")/24 * Transaction name
        Income:Checking                           -dollar amount
        Expenses:Insurance                         dollar amount


<a id="orgbdfb10f"></a>

# Directory settings

TODO add function to set image-width to **80%** of the window size.

    (after! org (setq org-image-actual-width nil
                      org-archive-location "~/.org/gtd/archives.org::datetree"
                      projectile-project-search-path '("~/projects/")))


<a id="org17a60fd"></a>

# Export Settings

    (after! org (setq org-html-head-include-scripts t
                      org-export-with-toc t
                      org-export-with-author t
                      org-export-headline-levels 4
                      org-export-with-drawers nil
                      org-export-with-email t
                      org-export-with-footnotes t
                      org-export-with-sub-superscripts nil
                      org-export-with-latex t
                      org-export-with-section-numbers nil
                      org-export-with-properties nil
                      org-export-with-smart-quotes t
                      org-export-backends '(pdf ascii html latex odt md pandoc)))

Embed images into the exported HTML files.

    (defun replace-in-string (what with in)
      (replace-regexp-in-string (regexp-quote what) with in nil 'literal))
    
    (defun org-html--format-image (source attributes info)
      (progn
        (setq source (replace-in-string "%20" " " source))
        (format "<img src=\"data:image/%s;base64,%s\"%s />"
                (or (file-name-extension source) "")
                (base64-encode-string
                 (with-temp-buffer
                   (insert-file-contents-literally source)
                  (buffer-string)))
                (file-name-nondirectory source))))


<a id="org20050c4"></a>

# Misc Org Mode settings

    (require 'org-id)
    (setq org-link-file-path-type 'relative)


<a id="orgaa31f79"></a>

# Keywords

After much feedback and discussing with other users, I decided to simplify the keyword list to make it simple. Defining a project will now focus on the tag word **:project:** so that all child task are treated as part of the project.

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Keyword</th>
<th scope="col" class="org-left">Description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">\TODO</td>
<td class="org-left">Task has actionable items defined and ready to be worked.</td>
</tr>


<tr>
<td class="org-left">HOLD</td>
<td class="org-left">Has actionable items, but is on hold due to various reasons.</td>
</tr>


<tr>
<td class="org-left">NEXT</td>
<td class="org-left">Is ready to be worked and should be worked on soon.</td>
</tr>


<tr>
<td class="org-left">DONE</td>
<td class="org-left">Task is completed and closed.</td>
</tr>


<tr>
<td class="org-left">KILL</td>
<td class="org-left">Abandoned or terminated.</td>
</tr>
</tbody>
</table>

    
    (custom-declare-face '+org-todo-active  '((t (:inherit (bold font-lock-constant-face org-todo)))) "")
    (custom-declare-face '+org-todo-project '((t (:inherit (bold font-lock-doc-face org-todo)))) "")
    (custom-declare-face '+org-todo-onhold  '((t (:inherit (bold warning org-todo)))) "")
    (custom-declare-face '+org-todo-next '((t (:inherit (bold font-lock-keyword-face org-todo)))) "")
    (custom-declare-face 'org-checkbox-statistics-todo '((t (:inherit (bold font-lock-constant-face org-todo)))) "")
    
      (setq org-todo-keywords
            '((sequence
               "TODO(t)"  ; A task that needs doing & is ready to do
               "PROJ(p)"  ; Project with multiple task items.
               "NEXT(n)"  ; Task is next to be worked on.
               "WAIT(w)"  ; Something external is holding up this task
               "|"
               "DONE(d)"  ; Task successfully completed
               "KILL(k)")) ; Task was cancelled, aborted or is no longer applicable
            org-todo-keyword-faces
            '(("WAIT" . +org-todo-onhold)
              ("PROJ" . +org-todo-project)
              ("TODO" . +org-todo-active)
              ("NEXT" . +org-todo-next)))


<a id="org4796c58"></a>

# Logging and Drawers

For the logging drawers, we like to keep our notes and clock history **seperate** from our properties drawer&#x2026;

    (after! org (setq org-log-state-notes-insert-after-drawers nil))

Next, we like to keep a history of our activity of a task so we **track** when changes occur, and we also keep our notes logged in **their own drawer**. Optionally you can also add the following in-buffer settings to override the `org-log-into-drawer` function. `#+STARTUP: logdrawer` or `#+STARTUP: nologdrawer`

    (after! org (setq org-log-into-drawer t
                      org-log-done 'time
                      org-log-repeat 'time
                      org-log-redeadline 'note
                      org-log-reschedule 'note))


<a id="orgcbb41bf"></a>

# Properties

    (setq org-use-property-inheritance t ; We like to inhert properties from their parents
          org-catch-invisible-edits 'error) ; Catch invisible edits


<a id="org47c61f2"></a>

# Publishing

REVIEW do we need to re-define our publish settings for the ROAM directory?

    (after! org (setq org-publish-project-alist
                      '(("attachments"
                         :base-directory "~/.org/"
                         :recursive t
                         :base-extension "jpg\\|jpeg\\|png\\|pdf\\|css"
                         :publishing-directory "~/publish_html"
                         :publishing-function org-publish-attachment)
                        ("notes-to-orgfiles"
                         :base-directory "~/.org/notes/"
                         :publishing-directory "~/notes/"
                         :base-extension "org"
                         :recursive t
                         :publishing-function org-org-publish-to-org)
                        ("notes"
                         :base-directory "~/.org/notes/"
                         :publishing-directory "~/nmartin84.github.io"
                         :section-numbers nil
                         :base-extension "org"
                         :with-properties nil
                         :with-drawers (not "LOGBOOK")
                         :with-timestamps active
                         :recursive t
                         :exclude "journal/.*"
                         :auto-sitemap t
                         :sitemap-filename "index.html"
                         :publishing-function org-html-publish-to-html
                         :html-head "<link rel=\"stylesheet\" href=\"https://raw.githack.com/nmartin84/raw-files/master/htmlpro.css\" type=\"text/css\"/>"
    ;                     :html-head "<link rel=\"stylesheet\" href=\"https://codepen.io/nmartin84/pen/RwPzMPe.css\" type=\"text/css\"/>"
    ;                     :html-head-extra "<style type=text/css>body{ max-width:80%;  }</style>"
                         :html-link-up "../"
                         :with-email t
                         :html-link-up "../../index.html"
                         :auto-preamble t
                         :with-toc t)
                        ("myprojectweb" :components("attachments" "notes" "notes-to-orgfiles")))))


<a id="org802da9b"></a>

# Refiling Defaults

TODO tweak refiling settings to match new GTD setup

    (after! org (setq org-refile-targets '((nil :maxlevel . 9)
                                           (org-agenda-files :maxlevel . 4))
                      org-refile-use-outline-path 'buffer-name
                      org-outline-path-complete-in-steps nil
                      org-refile-allow-creating-parent-nodes 'confirm))


<a id="orgeb565f8"></a>

# Orgmode Startup

    (after! org (setq org-startup-indented 'indent
                      org-startup-folded 'content
                      org-src-tab-acts-natively t))
    (add-hook 'org-mode-hook 'org-indent-mode)
    (add-hook 'org-mode-hook 'turn-off-auto-fill)


<a id="org6d856da"></a>

# Org Protocol

    (require 'org-roam-protocol)
    (setq org-protocol-default-template-key "d")


<a id="org0c387b0"></a>

# Default Tags

REVIEW should we define any additional tags?

    (setq org-tags-column 0)
    (setq org-tag-alist '((:startgrouptag)
                          ("Context")
                          (:grouptags)
                          ("@home" . ?h)
                          ("@computer")
                          ("@work")
                          ("@place")
                          ("@bills")
                          ("@order")
                          ("@labor")
                          ("@read")
                          ("@brainstorm")
                          ("@planning")
                          (:endgrouptag)
                          (:startgrouptag)
                          ("Categories")
                          (:grouptags)
                          ("vehicles")
                          ("health")
                          ("house")
                          ("hobby")
                          ("coding")
                          ("material")
                          ("goal")
                          (:endgrouptag)
                          (:startgrouptag)
                          ("Section")
                          (:grouptags)
                          ("#coding")
                          ("#research")))


<a id="org4b5cbf7"></a>

# Buffer Settings

    (global-auto-revert-mode 1)
    (setq undo-limit 80000000
          evil-want-fine-undo t
    ;      auto-save-default t
          inhibit-compacting-font-caches t)
    (whitespace-mode -1)
    
    (defun zyro/remove-lines ()
      "Remove lines mode."
      (display-line-numbers-mode -1))
    (remove-hook! '(org-roam-mode-hook) #'zyro/remove-lines)


<a id="org850df91"></a>

# Misc Settings

    (setq display-line-numbers-type t)
    (setq-default
     delete-by-moving-to-trash t
     tab-width 4
     uniquify-buffer-name-style 'forward
     window-combination-resize t
     x-stretch-cursor t)


<a id="org8a23669"></a>

# Module Settings


<a id="org53a3414"></a>

## company mode

    (after! org
      (set-company-backend! 'org-mode 'company-capf '(company-yasnippet company-org-roam company-elisp))
      (setq company-idle-delay 0.25))


<a id="org3b58d36"></a>

## Define Word

    (use-package define-word
      :config
      (map! :after org
            :map org-mode-map
            :leader
            :desc "Define word at point" "@" #'define-word-at-point))


<a id="orgac578cc"></a>

## Misc Modules [Bookmarks, PDF Tools]

Configuring PDF support and ORG-NOTER for note taking

    ;(use-package org-pdftools
    ;  :hook (org-load . org-pdftools-setup-link))


<a id="org0820dd7"></a>

## Graphs and Chart Modules

Eventually I would like to have org-mind-map generating charts like Sacha&rsquo;s [evil-plans](https://pages.sachachua.com/evil-plans/).

    (after! org (setq org-ditaa-jar-path "~/.emacs.d/.local/straight/repos/org-mode/contrib/scripts/ditaa.jar"))
    
    (use-package gnuplot
      :defer
      :config
      (setq gnuplot-program "gnuplot"))
    
    ; MERMAID
    (use-package mermaid-mode
      :defer
      :config
      (setq mermaid-mmdc-location "/node_modules/.bin/mmdc"
            ob-mermaid-cli-path "/node-modules/.bin/mmdc"))
    
    ; PLANTUML
    (use-package ob-plantuml
      :ensure nil
      :commands
      (org-babel-execute:plantuml)
      :defer
      :config
      (setq plantuml-jar-path (expand-file-name "~/.doom.d/plantuml.jar")))


<a id="orgee09d4b"></a>

## Elfeed

    (use-package elfeed-org
      :defer
      :config
      (setq rmh-elfeed-org-files (list "~/.elfeed/elfeed.org")))
    (use-package elfeed
      :defer
      :config
      (setq elfeed-db-directory "~/.elfeed/"))
    
    ;; (require 'elfeed-org)
    ;; (elfeed-org)
    ;; (setq elfeed-db-directory "~/.elfeed/")
    ;; (setq rmh-elfeed-org-files (list "~/.elfeed/elfeed.org"))


<a id="org9a25b46"></a>

## DEFT

When this variable is set to `t` your deft directory will be updated to your projectile-project root&rsquo;s folder when switching projects, and the deft buffer&rsquo;s contents will be refreshed.

    (setq deft-use-projectile-projects t)
    (defun zyro/deft-update-directory ()
      "Updates deft directory to current projectile's project root folder and updates the deft buffer."
      (interactive)
      (if (projectile-project-p)
          (setq deft-directory (expand-file-name (doom-project-root)))))
    (when deft-use-projectile-projects
      (add-hook 'projectile-after-switch-project-hook 'zyro/deft-update-directory)
      (add-hook 'projectile-after-switch-project-hook 'deft-refresh))

Configuring DEFT default settings

    (load! "my-deft-title.el")
    (use-package deft
      :bind (("<f8>" . deft))
      :commands (deft deft-open-file deft-new-file-named)
      :config
      (setq deft-directory "~/.org/"
            deft-auto-save-interval 0
            deft-recursive t
            deft-current-sort-method 'title
            deft-extensions '("md" "txt" "org")
            deft-use-filter-string-for-filename t
            deft-use-filename-as-title nil
            deft-markdown-mode-title-level 1
            deft-file-naming-rules '((nospace . "-"))))
    (require 'my-deft-title)
    (advice-add 'deft-parse-title :around #'my-deft/parse-title-with-directory-prepended)


<a id="org73671ab"></a>

## Org-Rifle

    (use-package helm-org-rifle
      :after (helm org)
      :preface
      (autoload 'helm-org-rifle-wiki "helm-org-rifle")
      :config
      (add-to-list 'helm-org-rifle-actions '("Insert link" . helm-org-rifle--insert-link) t)
      (add-to-list 'helm-org-rifle-actions '("Store link" . helm-org-rifle--store-link) t)
      (defun helm-org-rifle--store-link (candidate &optional use-custom-id)
        "Store a link to CANDIDATE."
        (-let (((buffer . pos) candidate))
          (with-current-buffer buffer
            (org-with-wide-buffer
             (goto-char pos)
             (when (and use-custom-id
                        (not (org-entry-get nil "CUSTOM_ID")))
               (org-set-property "CUSTOM_ID"
                                 (read-string (format "Set CUSTOM_ID for %s: "
                                                      (substring-no-properties
                                                       (org-format-outline-path
                                                        (org-get-outline-path t nil))))
                                              (helm-org-rifle--make-default-custom-id
                                               (nth 4 (org-heading-components))))))
             (call-interactively 'org-store-link)))))
    
      ;; (defun helm-org-rifle--narrow (candidate)
      ;;   "Go-to and then Narrow Selection"
      ;;   (helm-org-rifle-show-entry candidate)
      ;;   (org-narrow-to-subtree))
    
      (defun helm-org-rifle--store-link-with-custom-id (candidate)
        "Store a link to CANDIDATE with a custom ID.."
        (helm-org-rifle--store-link candidate 'use-custom-id))
    
      (defun helm-org-rifle--insert-link (candidate &optional use-custom-id)
        "Insert a link to CANDIDATE."
        (unless (derived-mode-p 'org-mode)
          (user-error "Cannot insert a link into a non-org-mode"))
        (let ((orig-marker (point-marker)))
          (helm-org-rifle--store-link candidate use-custom-id)
          (-let (((dest label) (pop org-stored-links)))
            (org-goto-marker-or-bmk orig-marker)
            (org-insert-link nil dest label)
            (message "Inserted a link to %s" dest))))
    
      (defun helm-org-rifle--make-default-custom-id (title)
        (downcase (replace-regexp-in-string "[[:space:]]" "-" title)))
    
      (defun helm-org-rifle--insert-link-with-custom-id (candidate)
        "Insert a link to CANDIDATE with a custom ID."
        (helm-org-rifle--insert-link candidate t))
    
      (helm-org-rifle-define-command
       "wiki" ()
       "Search in \"~/lib/notes/writing\" and `plain-org-wiki-directory' or create a new wiki entry"
       :sources `(,(helm-build-sync-source "Exact wiki entry"
                     :candidates (plain-org-wiki-files)
                     :action #'plain-org-wiki-find-file)
                  ,@(--map (helm-org-rifle-get-source-for-file it) files)
                  ,(helm-build-dummy-source "Wiki entry"
                     :action #'plain-org-wiki-find-file))
       :let ((files (let ((directories (list "~/lib/notes/writing"
                                             plain-org-wiki-directory
                                             "~/lib/notes")))
                      (-flatten (--map (f-files it
                                                (lambda (file)
                                                  (s-matches? helm-org-rifle-directories-filename-regexp
                                                              (f-filename file))))
                                       directories))))
             (helm-candidate-separator " ")
             (helm-cleanup-hook (lambda ()
                                  ;; Close new buffers if enabled
                                  (when helm-org-rifle-close-unopened-file-buffers
                                    (if (= 0 helm-exit-status)
                                        ;; Candidate selected; close other new buffers
                                        (let ((candidate-source (helm-attr 'name (helm-get-current-source))))
                                          (dolist (source helm-sources)
                                            (unless (or (equal (helm-attr 'name source)
                                                               candidate-source)
                                                        (not (helm-attr 'new-buffer source)))
                                              (kill-buffer (helm-attr 'buffer source)))))
                                      ;; No candidates; close all new buffers
                                      (dolist (source helm-sources)
                                        (when (helm-attr 'new-buffer source)
                                          (kill-buffer (helm-attr 'buffer source))))))))))
      :general
      (:keymaps 'org-mode-map
       "M-s r" #'helm-org-rifle-current-buffer)
      :custom
      (helm-org-rifle-directories-recursive t)
      (helm-org-rifle-show-path t)
      (helm-org-rifle-test-against-path t))
    
    (provide 'setup-helm-org-rifle)


<a id="org528fa08"></a>

## Pandoc

    (setq org-pandoc-options '((standalone . t) (self-contained . t)))


<a id="org4538107"></a>

## ROAM

These are my default ROAM settings

    (setq org-roam-tag-sources '(prop last-directory))
    (setq org-roam-db-location "~/.org/roam.db")
    (setq org-roam-directory "~/.org/")
    (add-to-list 'safe-local-variable-values
    '(org-roam-directory . "."))
    
    (setq org-roam-dailies-capture-templates
       '(("d" "daily" plain (function org-roam-capture--get-point) ""
          :immediate-finish t
          :file-name "journal/%<%Y-%m-%d-%a>"
          :head "#+TITLE: %<%Y-%m-%d %a>\n#+STARTUP: content\n\n")))
    
    (setq org-roam-capture-templates
            '(("b" "book" plain (function org-roam-capture--get-point)
               :file-name "book/${slug}%<%Y%m%d%H%M>"
               :head "#+TITLE: ${slug}\n#+roam_tags: %^{tags}\n\nsource :: [[%^{link}][%^{link_desc}]]\n\n"
               "%?"
               :unnarrowed t)
              ("c" "curiousity" plain (function org-roam-capture--get-point)
               :file-name "curious/${slug}"
               :head "#+TITLE: ${title}\n#+roam_tags: %^{roam_tags}\n\n"
               "%?"
               :unnarrowed t)
              ("d" "digest" plain (function org-roam-capture--get-point)
               "%?"
               :file-name "digest/${slug}"
               :head "#+title: ${title}\n#+roam_tags: %^{roam_tags}\n\nsource :: [[%^{link}][%^{link_desc}]]\n\n"
               :unnarrowed t)
              ("f" "fleeting" plain (function org-roam-capture--get-point)
               "%?"
               :file-name "fleeting/${slug}"
               :head "#+title: ${title}\n#+roam_tags: %^{roam_tags}\n\n"
               :unnarrowed t)
              ("p" "private" plain (function org-roam-capture--get-point)
               "%?"
               :file-name "private/${slug}"
               :head "#+title: ${title}\n"
               :unnarrowed t)
              ("x" "programming" plain (function org-roam-capture--get-point)
               :file-name "%<%Y%m%d%H%M%S>-${slug}"
               :head "#+title: ${title}\n#+roam_tags: %^{tags}\n- source :: [[%^{link}][%^{description}]] \\\n- metadata :: %?\n\n* Notes\n\n* Follow-up Actions"
               :unnarrowed t)
              ("r" "research" entry (function org-roam--capture-get-point)
               (file "~/.doom.d/templates/org-roam-research.org")
               :file-name "research/${slug}"
               "%?"
               :unnarrowed t)
              ("t" "technical" plain (function org-roam-capture--get-point)
               "%?"
               :file-name "technical/${slug}"
               :head "#+title: ${title}\n#+roam_tags: %^{roam_tags}\n\n"
               :unnarrowed t)))


<a id="org13b4324"></a>

## ROAM Server

    (use-package org-roam-server
      :ensure t
      :config
      (setq org-roam-server-host "192.168.1.82"
            org-roam-server-port 8070
            org-roam-server-export-inline-images t
            org-roam-server-authenticate nil
            org-roam-server-network-poll nil
            org-roam-server-network-arrows 'from
            org-roam-server-network-label-truncate t
            org-roam-server-network-label-truncate-length 60
            org-roam-server-network-label-wrap-length 20))


<a id="org8244406"></a>

## ROAM Export Backlinks + Content

    (defun my/org-roam--backlinks-list-with-content (file)
      (with-temp-buffer
        (if-let* ((backlinks (org-roam--get-backlinks file))
                  (grouped-backlinks (--group-by (nth 0 it) backlinks)))
            (progn
              (insert (format "\n\n* %d Backlinks\n"
                              (length backlinks)))
              (dolist (group grouped-backlinks)
                (let ((file-from (car group))
                      (bls (cdr group)))
                  (insert (format "** [[file:%s][%s]]\n"
                                  file-from
                                  (org-roam--get-title-or-slug file-from)))
                  (dolist (backlink bls)
                    (pcase-let ((`(,file-from _ ,props) backlink))
                      (insert (s-trim (s-replace "\n" " " (plist-get props :content))))
                      (insert "\n\n")))))))
        (buffer-string)))
    
    (defun my/org-export-preprocessor (backend)
      (let ((links (my/org-roam--backlinks-list-with-content (buffer-file-name))))
        (unless (string= links "")
          (save-excursion
            (goto-char (point-max))
            (insert (concat "\n* Backlinks\n") links)))))
    
    (add-hook 'org-export-before-processing-hook 'my/org-export-preprocessor)


<a id="org87ff447"></a>

## Reveal [HTML Presentations]

    (require 'ox-reveal)
    (setq org-reveal-root "https://cdn.jsdelivr.net/npm/reveal.js")
    (setq org-reveal-title-slide nil)


<a id="org0e97f81"></a>

## Super Agenda Settings

    (org-super-agenda-mode t)
    
    (setq org-agenda-custom-commands
          (quote (("N" "Notes" tags "NOTE"
                   ((org-agenda-overriding-header "Notes")
                    (org-tags-match-list-sublevels t)))
                  ("h" "Habits" tags-todo "STYLE=\"habit\""
                   ((org-agenda-overriding-header "Habits")
                    (org-agenda-sorting-strategy
                     '(todo-state-down effort-up category-keep))))
                  ("i" "Inbox"
                   ((tags "REFILE"
                          ((org-agenda-overriding-header "Tasks to Refile")
                           (org-tags-match-list-sublevels nil)))))
                  ("w" "Master Agenda"
                   ((agenda ""
                            ((org-agenda-span '1)
                             (org-agenda-files (append (file-expand-wildcards "~/.org/gtd/*.org")))
                             (org-agenda-start-day (org-today))))
                    (tags-todo "-CANCELLED/!"
                               ((org-agenda-overriding-header "Stuck Projects")
                                (org-agenda-skip-function 'bh/skip-non-stuck-projects)
                                (org-agenda-sorting-strategy
                                 '(category-keep))))
                    (tags-todo "-HOLD-CANCELLED/!"
                               ((org-agenda-overriding-header "Projects")
                                (org-agenda-skip-function 'bh/skip-non-projects)
                                (org-tags-match-list-sublevels 'indented)
                                (org-agenda-sorting-strategy
                                 '(category-keep))))
                    (tags-todo "-CANCELLED/!NEXT"
                               ((org-agenda-overriding-header (concat "Project Next Tasks"
                                                                      (if bh/hide-scheduled-and-waiting-next-tasks
                                                                          ""
                                                                        " (including WAITING and SCHEDULED tasks)")))
                                (org-agenda-skip-function 'bh/skip-projects-and-habits-and-single-tasks)
                                (org-tags-match-list-sublevels t)
                                (org-agenda-todo-ignore-scheduled bh/hide-scheduled-and-waiting-next-tasks)
                                (org-agenda-todo-ignore-deadlines bh/hide-scheduled-and-waiting-next-tasks)
                                (org-agenda-todo-ignore-with-date bh/hide-scheduled-and-waiting-next-tasks)
                                (org-agenda-sorting-strategy
                                 '(todo-state-down effort-up category-keep))))
                    (tags-todo "-SOMEDAY-REFILE-CANCELLED-WAITING-HOLD/!"
                               ((org-agenda-overriding-header (concat "Project Subtasks"
                                                                      (if bh/hide-scheduled-and-waiting-next-tasks
                                                                          ""
                                                                        " (including WAITING and SCHEDULED tasks)")))
                                (org-agenda-skip-function 'bh/skip-non-project-tasks)
                                (org-agenda-todo-ignore-scheduled bh/hide-scheduled-and-waiting-next-tasks)
                                (org-agenda-todo-ignore-deadlines bh/hide-scheduled-and-waiting-next-tasks)
                                (org-agenda-todo-ignore-with-date bh/hide-scheduled-and-waiting-next-tasks)
                                (org-agenda-sorting-strategy
                                 '(category-keep))))
                    (tags-todo "-SOMEDAY-REFILE-CANCELLED-#waiting-#hold-#monitor/!"
                               ((org-agenda-overriding-header (concat "Standalone Tasks"
                                                                      (if bh/hide-scheduled-and-waiting-next-tasks
                                                                          ""
                                                                        " (including WAITING and SCHEDULED tasks)")))
                                (org-agenda-skip-function 'bh/skip-project-tasks)
                                (org-agenda-todo-ignore-scheduled t)
                                (org-agenda-todo-ignore-deadlines t)
                                (org-agenda-todo-ignore-with-date t)
                                (org-agenda-sorting-strategy
                                 '(category-keep))))
                    (tags-todo "-CANCELLED+#waiting|#hold|#monitor/"
                               ((org-agenda-overriding-header (concat "Waiting and Postponed Tasks"
                                                                      (if bh/hide-scheduled-and-waiting-next-tasks
                                                                          ""
                                                                        " (including WAITING and SCHEDULED tasks)")))
                                (org-agenda-skip-function 'bh/skip-non-tasks)
                                (org-tags-match-list-sublevels nil)
                                (org-agenda-todo-ignore-scheduled bh/hide-scheduled-and-waiting-next-tasks)
                                (org-agenda-todo-ignore-deadlines bh/hide-scheduled-and-waiting-next-tasks)))
                    (tags "-REFILE/"
                          ((org-agenda-overriding-header "Tasks to Archive")
                           (org-agenda-skip-function 'bh/skip-non-archivable-tasks)
                           (org-tags-match-list-sublevels nil))))
                   nil))))


<a id="org688147c"></a>

# Loading secrets

    (let ((secrets (expand-file-name "secrets.el" doom-private-dir)))
    (when (file-exists-p secrets)
      (load secrets)))


<a id="orge36968c"></a>

# Hacks


<a id="org3f809b2"></a>

# Custom Functions

    (load! "customs.el")
    (load! "org-helpers.el")


<a id="org72dc77c"></a>

## Time Stamps

    (defun nm/org-insert-timestamp ()
      "Insert active timestamp at POS."
      (interactive)
      (insert (format "<%s> " (format-time-string "%Y-%m-%d %H:%M:%p"))))
    (map! :after org
          :map org-mode-map
          :localleader
          :prefix ("j" . "nicks functions")
          :desc "Insert timestamp at POS" "i" #'nm/org-insert-timestamp)


<a id="org7959977"></a>

## Capture Template File Picker

    (defun nm/org-capture-file-picker ()
      "Select a file from the PROJECTS folder and return file-name."
      (let ((file (read-file-name "Project: " "~/.org/gtd/projects/")))
        (expand-file-name (format "%s" file))))


<a id="orgd7c5bd4"></a>

## Clarify Tasks

Clarify task will take a list of property fields and pass them to `nm/org-clarify-task-properties` to update task items which are missing those property fields.

    (defun nm/org-get-headline-property (arg)
      "Extract property from headline and return results."
      (interactive)
      (org-entry-get nil arg t))
    
    (defun nm/org-get-headline-properties ()
      "Get headline properties for ARG."
      (org-back-to-heading)
      (org-element-at-point))
    
    (defun nm/org-get-headline-title ()
      "Get headline title from current headline."
      (interactive)
      (org-element-property :title (nm/org-get-headline-properties)))
    
    ;;;;;;;;;;;;--------[ Clarify Task Properties ]----------;;;;;;;;;;;;;
    
    (defun nm/update-task-tags ()
      "Update all child tasks in buffer that are missing a TAG value."
      (interactive)
      (org-show-all)
      (while (not (eobp))
        (progn
          (outline-next-heading)
          (org-narrow-to-subtree)
          (unless (eobp)
            (if (and (oh/is-task-p) (null (org-get-tags)))
                (counsel-org-tag)))
          (widen))))
    
    (setq org-tasks-properties-metadata (list "SOURCE"))
    
    (defun nm/org-clarify-task-properties (arg)
      "Update the metadata for a task headline."
      (unless (equal major-mode 'org-mode)
        (error "Not visiting an org-mode buffer."))
      (save-restriction
        (save-excursion
          (org-show-all)
          (goto-char (point-min))
          (let ((props arg))
            (while (not (eobp))
              (outline-next-heading)
              (org-narrow-to-subtree)
              (unless (eobp)
                (when (or (and (oh/is-project-p) (oh/is-todo-p)) (and (oh/is-task-p) (null (oh/has-parent-project-p)) (null (oh/has-subtask-p))))
                  (mapcar (lambda (props)
                            (when (null (org-entry-get nil (upcase props) t))
                              (org-set-property (upcase props) (org-read-property-value (upcase props))))) props))
                (when (and (oh/is-todo-p) (not (oh/is-task-p)))
                  (org-todo "PROJ"))
                (widen)))))))
    
    (defun nm/org-assign-tasks-proj ()
      "Scans buffer and assigns all tasks that contain child-tasks the PROJ keyword and vice versa."
      (interactive)
      (save-excursion
        (goto-line 1)
        (while (not (eobp))
          (outline-next-heading)
          (unless (eobp)
            (when (and (oh/is-todo-p) (not (oh/is-task-p)))
              (org-todo "PROJ"))
            (when (and (equal (org-get-todo-state) "PROJ") (oh/is-task-p))
              (org-todo "TODO"))
            (nm/org-set-next-state)))))
    
    (defun nm/org-checkbox-exist-p ()
      "Checks if a checkbox that's not marked DONE exist in the tree."
      (interactive)
      (org-back-to-heading)
      (let ((end (save-excursion (org-end-of-subtree t))))
        (search-forward-regexp "^[-+] \\[\\W].+\\|^[1-9].\\W\\[\\W]" end t)))
    
    (defun nm/org-checkbox-done-exist-p ()
      "Checks if a checkbox that's not marked DONE exist in the tree."
      (interactive)
      (org-back-to-heading)
      (let ((end (save-excursion (org-end-of-subtree t))))
        (search-forward-regexp "^[-+] \\[X].+\\|^[1-9].\\W\\[X]" end t)))
    
    (add-hook 'before-save-hook #'nm/org-assign-tasks-proj)
    
      (defun nm/org-clarify-metadata ()
        "Runs the clarify-task-metadata function with ARG being a list of property values."
        (interactive)
        (nm/org-clarify-task-properties org-tasks-properties-metadata))
    
      (map! :after org
            :map org-mode-map
            :localleader
            :prefix ("j" . "nicks functions")
            :desc "Clarify properties" "c" #'nm/org-clarify-metadata)


<a id="org2948d1f"></a>

## Capture headline finder

    (defun nm/org-capture-system ()
      "Capture stuff."
      (interactive)
      (save-restriction
        (let ((org-capture-templates
               '(("h" "headline capture" entry (function counsel-outline)
                  "* %?" :empty-lines-before 1 :empty-lines-after 1)
                 ("p" "plain capture" plain (function end-of-buffer)
                  "<%<%Y-%m-%d %H:%M>> %?" :empty-lines-before 1 :empty-lines-after 1))))
          (find-file-other-window (read-file-name "file: " "~/.org/"))
          (if (counsel-outline-candidates)
              (org-capture nil "h"))
          (org-capture nil "p"))))
    
    (defun nm/org-capture-to-file ()
      "Capture stuff."
      (interactive)
      (save-restriction
        (let ((org-capture-templates
               '(("h" "headline capture" entry (function counsel-outline)
                  "* %?" :empty-lines-before 1 :empty-lines-after 1)
                 ("p" "plain capture" plain (function end-of-buffer)
                  "<%<%Y-%m-%d %H:%M>> %?" :empty-lines-before 1 :empty-lines-after 1))))
          (org-capture nil "h"))))
    
    (bind-key "<f7>" #'nm/org-capture-to-file)
    
    (defun nm/org-capture-weeklies ()
      "Find weeklies file and call counsel-outline."
      (interactive)
      (org-open-file "~/.org/gtd/weeklies.org")
      (counsel-outline))
    
    (defun nm/org-end-of-headline()
      "Move to end of current headline"
      (interactive)
      (outline-next-heading)
      (forward-char -1))


<a id="org2936ccd"></a>

## Search file headlines and send tree to indirect buffer

    ; TODO Write function that takes a file as input from user, then returns a searchable headline list and narrows the results to a indirect buffer.


<a id="org64e390b"></a>

## Change Font

    (defun nm/emacs-change-font ()
      "Change font based on available font list."
      (interactive)
      (let ((font (ivy-completing-read "font: " (font-family-list))))
        (setq doom-font (font-spec :family font :size 18)
              doom-big-font (font-spec :family font :size 24)))
      (doom/reload-font))


<a id="org9080b23"></a>

# Theme Settings

    ;(after! org (toggle-frame-maximized)
      (setq doom-theme 'doom-solarized-dark)
    (defun nm/adjust-frame-size ()
      "set frame size accordingly."
      (set-frame-size (selected-frame) 130 65))
    (nm/adjust-frame-size)

