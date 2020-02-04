# Создание своего репозитория для Helm

## Github
1. Создать репозиторий на github с веткой gh-pages
```
{
    git checkout -b gh-pages
    git push --set-upstream origin gh-pages
}
```
2. Запаковать чарт
```helm package viberr```
3. Перейти на GitHub, в разделе settings нужного репозитория найти Github Pages, взять url
```https://revolman.github.io/helm```
4. Проиндексировать репозиторий. Cоздастся файл index.yaml. Запушить репозиторий.
```
{
    helm repo index . --url https://revolman.github.io/helm
    git add .
    git comit -am "Обновил индекс"
    git push origin
}
```
### Использование репозитория
1. Добавить репозиторий
```
helm repo add <repo_name> <url>
helm repo update
```
url: https://revolman.github.io/helm
2. Установка из репозиторий
```
helm install viberr my-helm/viberr
или
helm pull my-helm/viberr
или
helm fetch my-helm/viberr --version=0.1.4
```
3. Безопасная установка с откатом в kubernetes
```
helm upgrade --install --atomic viberr ./viberr/ -n staging
```