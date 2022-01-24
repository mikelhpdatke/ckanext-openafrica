Phiên bản giao diện này chạy ổn định trên ckan 2.7

Nếu chưa có mã nguồn ckan2.7 có thể lấy mã nguồn tại https://gitlab.com/ais-research/bien-dao/ckan-2.8.git (chuyển sang nhánh có 2.7)

Thêm đoạn code sau vào Dockerfile trong thư mục có đường dẫn /ckan/Dockerfile trong repo của bạn

```
RUN pip install -e git+https://github.com/mikelhpdatke/ckanext-openafrica.git@new_theme_hot_fix#egg=ckanext-openafrica
RUN cp src/ckanext-openafrica/logo.png src/ckan/ckan/public/base/images/logo.png
RUN cp src/ckanext-openafrica/favicon_vasi.ico src/ckan/ckan/public/base/images/favicon_vasi.ico
RUN paster --plugin=ckan config-tool ${APP_DIR}/production.ini "ckan.favicon = /base/images/favicon_vasi.ico"
RUN paster --plugin=ckan config-tool ${APP_DIR}/production.ini "ckan.site_logo = /base/images/logo.png"
```

Thêm openafrica vào cấu hình ckan.plugins của ckan trong /ckan/Dockerfile.
