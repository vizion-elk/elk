# kibana create user help

## Step 1. 
Login to kibana with elastic account,the kibana url and es app url are as below:
```css
Kibana URL: https://vzg6dlns1d2ofekcd1-kibana.es5.vizion.ai:443/kibana770
Username: elastic
Password: bgcmnduqpgax12hi
Elasticsearch API Endpoint: https://elastic:bgcmnduqpgax12hi@vzg6dlns1d2ofekcd1.es5.vizion.ai:443
```

## Step 2. 
Click 'Security' -> 'Roles' -> Click 'Add' icon -> Input 'Role name' such as:metricrole:

1) Click 'Cluster Permission' -> Click 'Add Action Group' to select following permissions:
    ```css
    cluster_monitor
    ODS_CLUSTER_MANAGE_INDEX_TEMPLATES
    ODS_CLUSTER_MANAGE_PIPELINES
    ```

   Then Check the 'Show Advanced' checkbox -> Click 'Add Single Permission' button to add following permissions:
    ```css
    indices:data/write/index
    indices:data/write/bulk
    ```
2) Click 'Index Permissions' > Click 'Add Index Permissions' -> Input 'Index Pattern' as: metricbeat* -> Click 'Add Action Group' to select following permissions:
    ```css
    create_index
    index
    manage
    read
    ```
3) Click 'Tenant permissions' tab -> Click 'Add tenant permission' button -> Input tenant pattern 'global' -> Click 'Add Field' -> Select 'kibana_all_read' and 'kibana_all_write'

   Then click 'Save Role Definition' to create the role

### Step 3.
Click 'Security' -> Click 'Internal User Database' -> Click 'Add' icon -> Input 'Username' such as:metricuser,and input password:password ->
Click 'Add Role' to select the newly added 'metricuser' and 'kibana_user' -> Click "Submit" to create the user

### Step 4.
Click 'Security' -> Click 'Role Mappings' -> Click 'Add' button -> Select the newly added role:metricrole -> Click 'Add User' button ->
Input the newly added user:metricuser to save the mapping

### Step 5.
Then you can login to kibana and start beat with the new beat user: metricuser / password:
 ```css
Kibana URL: https://vzg6dlns1d2ofekcd1-kibana.es5.vizion.ai:443/kibana770
Username: metricuser
Password: password
Elasticsearch API Endpoint: https://metricuser:password@vzg6dlns1d2ofekcd1.es5.vizion.ai:443
```