# Setting up a Jupyter Book Workflow is not easy
- [[Setting up a Jupyter Book Workflow is not easy]]

Note added: 20210720-1807

#NoSummary #writingprocess #JupyterBook

- [Setup Git, Bash, and Conda on Your Computer | Earth Data Science - Earth Lab](https://www.earthdatascience.org/workshops/setup-earth-analytics-python/setup-git-bash-conda/) 
		- install bash to non-C (opt)
		- bash+git could(?) be portable; conda must(?) be installed
		- edit ~home\bash_profile to make sure pointing to /path/to/conda.exe 
	- [Overview](https://jupyterbook.org/start/overview.html) 
		- cd /h/path/to/mynewbook
		- conda create book_name pip
		- conda activate book_name
		- conda create --prefix ./envs
		- pip install -U jupyter-books
		- jupyter-book create mynewbook
			- pay attention to pywin32 and /path/to/pywin32 - can require a lot of cd'ing
		- find it at ~home\mynewbook
	- [Publish your book online](https://jupyterbook.org/start/publish.html)
		- Create an online repository for your book - to connect hosted book with source content > put book’s source content in a public repo
			- [Sign in to GitHub · GitHub](https://github.com/new) > create new repo
			- name; description; make public; Do not initialize it with a README file - click on License (pick one)(?) or .gitignore (pick Python)(?); create
			- clone (currently empty) online repo to a location on local computer - git clone https://github.com/<my-org>/<my-repository-name>
			- copy book files and folders into cloned repository - cp -r mylocalbook/* myonlinebook/
			- sync local and online repositories - cd myonlinebook \git add ./*\git commit -m "adding my first book!"\git push
				- may be issues with [Setting your commit email address - GitHub Docs](https://docs.github.com/en/github/setting-up-and-managing-your-github-user-account/managing-email-preferences/setting-your-commit-email-address) see also: [git - Meaning of the GitHub message: push declined due to email privacy restrictions - Stack Overflow](https://stackoverflow.com/questions/43378060/meaning-of-the-github-message-push-declined-due-to-email-privacy-restrictions); [git - Error "Your push would publish a private email address" - Stack Overflow](https://stackoverflow.com/questions/43863522/error-your-push-would-publish-a-private-email-address/51097104#51097104)
		- publish with GitHub Pages - pushed the _source files_ for our book into our GitHub repository; next, publish the _build artifact_ of book online > rendered as website
			- pip install ghp-import
			- update Settings > Pages: Use `gh-pages` branch (after next step); choose root directory `/` (book only; if documentation as part of application, use '/docs')
			- `main` branch local book root (which should contain the `_build/html` folder) > ghp-import -n -p -f _build/html
			- return to Settings > Pages: set to `gh-pages`, get URL.  About > description and URL
			- To update, changes to local book’s content on the `main` branch of your local repo, re-build `jupyter-book build mybookname/` and then push `ghp-import -n -p -f mylocalbook/_build/html`
