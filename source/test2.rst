###########################
複雑な図を描く
###########################

blockdiag Pluginを利用したフロー図の描画
===========================================

.. blockdiag::
   
   blockdiag {
 
    internet [shape="cloud"];
    firewall[label="firewall\n(shared)"];
    vip_lb[label="VIP",shape="beginpoint"];
    keepalived_lb01[label="keepalived"];
    keepalived_lb02[label="keepalived"];
    keepalived_lb01 -- vip_lb[folded];
    keepalived_lb02 -- vip_lb[folded];
 
    proxy_web01[label="proxy"];
    apache_web01[label="apache+php"];
    disk_web01[label="disk",shape=flowchart.database];
    proxy_web01     -> apache_web01;
    apache_web01    -> disk_web01[folded];
 
    proxy_web02[label="proxy"];
    apache_web02[label="apache+php"];
    disk_web02[label="disk",shape=flowchart.database];
    proxy_web02     -> apache_web02;
    apache_web02    -> disk_web02[folded];
 
    mysql_db01[label="mysql\n(master)",shape=flowchart.database];
    mysql_db02[label="mysql\n(slave)",shape=flowchart.database];
    mysql_db01  -> mysql_db02[folded,label="replication"];
 
    internet    -> firewall -> vip_lb;
    vip_lb      -> proxy_web01,proxy_web02;
    apache_web01,apache_web02 -> mysql_db01[label="insert/update"];
    apache_web01,apache_web02 -> mysql_db02[label="select"];
    disk_web01  -> disk_web02 [folded,label="rsync"];
 
    group lb_group {
        color="#882222";
        textcolor="#660000";
        shape=line;
        style=dashed;
        label="Clusterd Load Balncer";
        group lb01_group{label="lb01";keepalived_lb01;};
        vip_lb;
        group lb02_group{label="lb02";keepalived_lb02;};
        };
    group production_group { 
        color="#882222";
        textcolor="#660000";
        shape=line;
        style=dashed;
        label="production";
        group web01_group{label="web01";proxy_web01;apache_web01;disk_web01};
        group web02_group{label="web02";proxy_web02;apache_web02;disk_web02};
        group db01_group{label="db01";mysql_db01;};
        group db02_group{label="db02";mysql_db02;};
        };
 
    stg-proxy_web01[label="proxy"];
    stg-apache_web01[label="apache"];
    stg-disk_web01[label="disk",shape=flowchart.database];
    stg-apache_web01    -> stg-disk_web01[folded];
 
    stg-mysql_db01[label="mysql",shape=flowchart.database];
    vip_lb  -> stg-proxy_web01;
    stg-proxy_web01 -> stg-apache_web01;
    stg-apache_web01   -> stg-mysql_db01;
 
    group staging_group { 
        color="#882222";
        textcolor="#660000";
        shape=line;
        style=dashed;
        label="staging";
        group stg-web01_group{label="stg-web01";stg-proxy_web01;stg-apache_web01;stg-disk_web01};
        group stg-db01_group{label="stg-db01";stg-mysql_db01;};
        };
 
   }

