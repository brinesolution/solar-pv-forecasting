# GitHub Upload Steps

Run these commands from this folder after choosing the GitHub repository name and visibility.

```powershell
cd P:\Project_Solar\10_github_publication_release\solar-pv-forecasting-appendix-artifacts
git init
git status
git add .
git commit -m "Add solar PV forecasting appendix artifacts"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repository-name>.git
git push -u origin main
```

Before pushing, check:

```powershell
git status
git lfs ls-files
```

Git LFS is not required for the current package if all files remain below GitHub's 100 MB single-file limit. If GitHub reports any file-size issue, move that file to Git LFS or to a research-data host such as Zenodo, Figshare, OSF, or an institutional repository.

After upload, update:

- `CITATION.cff` with the final GitHub URL or repository DOI.
- The manuscript appendix with the final repository URL and access date.
- `README.md` if the repository name or paper title changes.
