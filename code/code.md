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


## Learn this    

-   Markdown - [https://www.markdowntutorial.com/](https://www.markdowntutorial.com/)
-   Git (**expected time: half day)** - finish the quick guide. Show the result to your mentor. [http://rogerdudler.github.io/git-guide/](http://rogerdudler.github.io/git-guide/). If you are on Windows, we suggest using [Git Bash](https://git-scm.com/downloads). DO NOT USE ANY GUI.
        -   Create a dummy repo on github.
        -   Create a [README](https://help.github.com/articles/about-readmes/) file in your repo.
        -   Create a [pull request](https://help.github.com/articles/about-pull-requests/) on github. You will be asked to use this later.

Assuming you use [VS Code](https://code.visualstudio.com/) (Please don't use Sublime Text/Pycharm unless you're paying for it!).

## Must have addons

* [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)
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
