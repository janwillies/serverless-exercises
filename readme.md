This is a static website with exercises wrt serverless programming on Kubernetes (with kubeless)

Install hugo
```
brew install hugo
```

Install theme
```
git clone https://github.com/vjeantet/hugo-theme-docdock.git themes/hugo-theme-docdock
```

Run local hugo server
```
hugo server --theme=hugo-theme-docdock --buildDrafts
```