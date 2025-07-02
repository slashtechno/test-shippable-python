# Simple, shippable Python projects  

## A disclaimer  
Ideally, learn [uv](https://docs.astral.sh/). It will allow you to manage dependencies much more easily while ensuring every project has a unique virtual environment. In addition, it will allow you to [build and publish to PyPI](https://docs.astral.sh/uv/guides/package/), so people can install your project with a simple `pip install <your project>`.  

The setup in this repository is more for when you're at a hackathon or need to quickly ship a project that can easily be experienced by others—a major requirement for [Hack Club](https://hackclub.com) YSWS programs. You can take an existing Python project and should be able to quickly compile it so it can run on most Windows, macOS (only ARM/M-series), and Linux machines with a simple click.

Hi! If you're a beginner to Python, you might wonder: how do you get your projects to run on other machines?

## If you're already done with your project (quick and easy)  
Already have a project and GitHub repo and don't want to release it via uv? Copy `nukita.yml` from `.github/workflows` in this repo and put it in `.github/workflows` in your repository. Then, go to https://github.com/USERNAME/REPO/settings/actions and set Workflow permissions to `Read and write permissions`.

## The "proper" way
A simple introduction to [uv](https://docs.astral.sh/uv) and pyproject.toml:
1. Create a [PyPI](https://pypi.org/) account.
    - You can use your GitHub account to sign up for PyPI.
    - If it's your first time publishing a package, it's recommended to try publishing a test package on [test.pypi.org](https://test.pypi.org/). Make sure to set the index URL and run `uv publish --index testpypi` if you want to publish to test.pypi.org.
    ```toml
    [[tool.uv.index]]
    name = "testpypi"
    url = "https://test.pypi.org/simple/"
    publish-url = "https://test.pypi.org/legacy/"
    explicit = true
    ```
2. Get a token from PyPI.
    - Go to https://pypi.org/manage/account/token/ and create a token.
    - You'll use this as your password for PyPI and `__token__` as your username.
3. Install [uv](https://docs.astral.sh/uv/getting-started/installation/).
4. Run `uv init project_name --package`.
5. Change directory to the project with `cd project_name`.
6. Install dependencies with `uv add <dependencies>`.
    - DON'T USE `pip install <dependencies>`!
7. Edit `src/project_name/__main__.py` and make it execute whatever you want, including functions from other files in your package.
    - For example, you can import `src/project_name/utils.py` from `src/project_name/__main__.py` with `from project_name import utils`.
8. Edit project metadata in `pyproject.toml`.
9. To run your program, run `uv run project_name`.
10. Build your project with `uv build`.
11. Use your credentials from PyPI to publish your project to PyPI with `uv publish`.
12. Go to PyPI and you'll see your project there! For Hack Club YSWS programs, you can use this as your playable URL.