# Tutorial-Duplicate-ERPNext-site

My use case is I want to duplicate site from staging-erp.aaa.com to erp.aaa.com and keep all the config and setting. So when staging-erp.aaa.com will be still running and will be use for testing and training and erp.aaa.com will be use for real transaction.

An additional step might be need to properly setup nginx domain, it’s depends on each setup.

#Create new site#
```
bench new-site erp.aaa.com
```

#Copy site database#
```
Site database name locate at bench/sites/site_name/site_config.json
```
```
mysqldump -h'mariadb' -u'root' -p source_database_name > site_data.sql
mysql -h'mariadb' -u'root' -p target_database_name < site_data.sql
```

#Copy site file#
```
rm -rf sites/erp.aaa.com/private/
rm -rf sites/erp.aaa.com/public/
cp -r sites/staging-erp.aaa.com/private/ sites/erp.aaa.com/private
cp -r sites/staging-erp.aaa.com/public/ sites/erp.aaa.com/public
```
