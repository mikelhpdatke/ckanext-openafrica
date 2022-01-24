Phiên bản giao diện này chạy ổn định trên ckan 2.7

Thêm đoạn code sau vào Dockerfile trong thư mục có đường dẫn /ckan/Dockerfile trong repo của bạn

```
RUN pip install -e git+https://github.com/mikelhpdatke/ckanext-openafrica.git@new_theme#egg=openafrica
RUN cp src/openafrica/logo.png src/ckan/ckan/public/base/images/logo.png
RUN cp src/openafrica/favicon_vasi.ico src/ckan/ckan/public/base/images/favicon_vasi.ico
RUN paster --plugin=ckan config-tool ${APP_DIR}/production.ini "ckan.favicon = base/images/favicon_vasi.ico"
RUN paster --plugin=ckan config-tool ${APP_DIR}/production.ini "ckan.site_logo = base/images/logo.png"
```
