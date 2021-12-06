**Two Laws of Software Engineering:** 
At RedCarpet we believe in two sacrosanct laws of software engineering. These can never be violated. Make sure you memorize these.
1.  "*It is much harder to read code than to write it*" - Anyone can write code. Very few can read code. The popular opinion is that "Creating a new software project is the impactful work. Fixing bugs is boring". The reality is that - fixing bugs is not boring. It is much harder since you need to read existing code and understand it. A hundred monkeys can write the code that you can. But only a great engineer can read code. It is very easy to write code/proposals/designs. It is very hard to read someone else's code/proposals/designs. At RedCarpet we recognize that a lot of poor decisions that are made is because of this problem.
    - Corollary - The more code you read, the better engineer you become. Read a lot of code on Github.
    -  Make it easy to read code. Write testcases.
2.  "*Premature complexity is the root of all evil*" - Only write as much code as is required to solve the problem. Dont build something extra to make it look "cooler". Dont use Tensorflow if a python script is sufficient.
    -  Corollary - never tell us "*I have written the code, but not run it*". If you have written one line/function of code, you better have run it.

# Reading code is hard. Why is it so hard to see code from 5 minutes ago ?
[http://www.cs.cmu.edu/~NatProg/papers/p101-yoon-VLHCC2014.pdf](Why is it so hard to see code from 5 minutes ago)
>A study found that Java developers backtracked every 6 minutes, meaning.. by clicking undo or pressing Ctrl-Z.

Answer: **Spend time in setting up tools - editor, debugger, etc. They are more important than writing code**


## 🐉🐉🐉 Never Ever Ever Ever EVER mess with dates/times, unicode and floating-point/decimal 🐉🐉🐉

Read some of these threads
- https://news.ycombinator.com/item?id=26282742 versus https://news.ycombinator.com/item?id=10195947 vs https://news.ycombinator.com/item?id=14179783
- https://lucumr.pocoo.org/2014/1/5/unicode-in-2-and-3/ vs https://news.ycombinator.com/item?id=18154667
- https://en.wikipedia.org/wiki/IEEE_754

Never EVER try to do these 3 things by hand. Use a library. Or you will suffer a lot. Very painfully.


## Git basics, etc 

- Pull Request [https://www.youtube.com/watch?v=XmIlJYdBgvc](https://www.youtube.com/watch?v=XmIlJYdBgvc)

- Git & Github [https://www.youtube.com/playlist?list=PL3Y9MECuxct0RMwdYcqoIjo-7ncRpTNLs](https://www.youtube.com/playlist?list=PL3Y9MECuxct0RMwdYcqoIjo-7ncRpTNLs)
-  Markdown - [https://www.markdowntutorial.com/](https://www.markdowntutorial.com/)
-  configuration for GitHub Desktop on Windows assumes CRLF but the text editor may be using LF. You can change your local repository settings to use lf instead 
```
git config core.eol lf
git config core.autocrlf input
```

**how to create a ssh key for github**
`ssh-keygen -t ed25519 -C "email-address-that-you-used@github.com"`

this will ask you for a filename and creates two files: `filename` and `filename.pub` . These two files are used in different places. Be careful. (`.pub` files are set outside - share with your company, set in github, etc. never share the `filename` itself)

set this `filename.pub` key in github - [https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

set this in your `~/.ssh/config`

```
Host github-redcarpet
   HostName github.com
   IdentityFile  ~/.ssh/filename
   IdentitiesOnly yes
```
This basically means that use `filename` whenever a url named `github-redcarpet` is seen in any repository. This will mean your git command will automatically choose the correct ssh secret key to connect.

normally you would add a new repo (or clone it) using `github.com`. But now you should use `github-redcarpet`. E.g.

`git remote add origin git@github-redcarpet:redcarpetup/myrepo.git`

or

`git clone git@github-redcarpet:redcarpetup/myrepo.git`



Assuming you use [VS Code](https://code.visualstudio.com/) (Please don't use Sublime Text/Pycharm unless you're paying for it!).

## Must have addons

* [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance). https://www.youtube.com/watch?v=mt91AHxUyMw&t=959s
* [ErrorLens](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens)

## Good to have addons

* [Bracket Pair Colorizer](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer)
* [Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)
* [Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
* [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)

## How to

Add the contents of settings.json to your current [settings.json](https://code.visualstudio.com/docs/getstarted/settings#_settings-file-locations). Restart VS Code for Magic.

## API Design
* [Stripe’s payments APIs: the first ten years](https://stripe.com/blog/payment-api-design)
* [Idempotency](https://www.moderntreasury.com/journal/why-idempotency-matters-in-payments)
