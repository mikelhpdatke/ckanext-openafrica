Thêm đoạn code sau vào Dockerfile ckan2.8/ckan/Dockerfile

```
RUN pip install -e git+https://github.com/mikelhpdatke/ckanext-openafrica.git@new_theme#egg=openafrica
RUN cp src/openafrica/logo.png src/ckan/ckan/public/base/images/logo.png
RUN cp src/openafrica/favicon_vasi.ico src/ckan/ckan/public/base/images/favicon_vasi.ico
RUN paster --plugin=ckan config-tool ${APP_DIR}/production.ini "ckan.favicon = base/images/favicon_vasi.ico"
RUN paster --plugin=ckan config-tool ${APP_DIR}/production.ini "ckan.site_logo = base/images/logo.png"
```
