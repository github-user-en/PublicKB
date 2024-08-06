> [!info] References:
> - [Jupytext Github](https://github.com/mwouts/jupytext)
> - [Explaining how to use Jupytext for collaborative editing of notebooks with Git](https://www.youtube.com/watch?v=J5yW-NEJp5Q)
> - [Marc Wouts - Jupytext: Jupyter Notebooks as Markdown Documents | JupyterCon 2020](https://www.youtube.com/watch?v=SDYdeVfMh48)

Jupytext makes it easier for your jupyter notebooks to interact with Git and other version control systems. The idea is that instead of syncing the `.ipynb` jupyter notebook, you can sync either its `.py` variant, or its `.md` variant.

This is especially useful when your notebook's markdown has images. In this case, when you change the image and then sync the notebook, comparing the changes between your notebook's local and remote variants will be a nightmare. Not only would it show the code changes, but also the image's binary code.

The key to being able to use the Jupytext plugin effectively is:
1. To not add the notebook to your git repo;
2. Instead, add either its corresponding `.py` or `.md` file to git's version control;
3. And, to know which alternative will be correct to use in which situation. 
   (For this, see Marc Wouts' video in the references above)
