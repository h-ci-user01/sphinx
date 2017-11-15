##################################
システム概要図を描画する
##################################


blockdiag Pluginを利用したシステム概要図の描画
===============================================


.. blockdiag::

  blockdiag {

  // Set fontsize
  default_fontsize = 12;  // default value is 11

  // set default colors
  default_node_color = lightblue;
  default_group_color = blue;
  default_linecolor = blue;
  default_textcolor = black;

    // standard node shapes
    A1 [shape = box,label = "リポジトリ管理(マスタ)システム"];
    A2 [shape = box,label = "課題管理（課題共有）システム"];
    A3 [shape = box,label = "チャット通知フレームワーク"];
    A4 [shape = box,label = "チャットサービス"];

    group lab1-1 {
     label = "Lab開発環境";
     color = "#87cefa";
     //shape = line;
     Dummy1 [label = " ", linecolor = white, color = white, shape = dots, width = 200, height = 20];
      group lab2-1 {
       //shape = line;
       color = white;
        group lab3-1 {
           label = "プロジェクト用リポジトリサーバ";
           color = "#d3d3d3";
           A1;
        }
        group lab3-2 {
           label = "課題管理用サーバ";
           color = "#d3d3d3";
           A2;
        }
      }
      group lab2-2 {
       //shape = line;
       color = white;
        group lab3-3 {
           label = "チャットサービス連携";
           color = "#d3d3d3";
           A3;
        }
      }
    }


    internet [shape = cloud];

    group lab1-2 {
     label = "外部SaaS";
     color = cadetblue;
     Dummy2 [label = " ", linecolor = white, color = white, shape = dots, width = 130, height = 20];
        group lab3-4 {
           label = "チャットサービス";
           color = "#d3d3d3";
           A4;
        }
    }
    A1 -- A2 -- A3 -- A4;
    Dummy1 -- internet;
    Dummy2 -- internet;
    Dummy3 -- internet;

    // standard node shapes
    B [shape = roundedbox,label = "ビルド・デプロイ環境"];
    C [shape = roundedbox,label = "ローカル開発環境"];
    D [shape = roundedbox,label = "デプロイ・テスト"];
    E [shape = roundedbox,label = "ドキュメント作成"];
    

    F [shape = roundedbox,label = "GitLab"];
    G [shape = roundedbox,label = "Redmine"];
    H [shape = roundedbox,label = "チャットサービス"];
    
    
    I1 [shape = box,label = "nginx",width =100,height = 100];
    I2 [shape = box,label = "postgresql",width =100,height = 100];
    I3 [shape = box,label = "redis",width =100,height = 100];
    I4 [shape = box,label = "elastic search",width =100,height = 100];
    I5 [shape = box,label = "rabbitmq",width =100,height = 100];
    I6 [shape = box,label = "web",width =100,height = 100];
    I7 [shape = box,label = "static",width =100,height = 100];
    
    
    J1 [shape = box,label = "postgresql",width =100,height = 100];
    J2 [shape = box,label = "redis",width =100,height = 100];
    J3 [shape = box,label = "elastic search",width =100,height = 100];
    J4 [shape = box,label = "rabbitmq",width =100,height = 100];
    J5 [shape = box,label = "web",width =100,height = 100];
    J6 [shape = box,label = "celery",width =100,height = 100];
    

    group hi1-1 {
     label = "開発環境";
     color = crimson;
     //shape = line;
     Dummy3 [label = " ", linecolor = white, color = white, shape = dots, width = 130, height = 20];
     
      group hi2-1 {
       label = "開発用サーバ";
       //shape = line;
       color = "#778899";
       Dummy4 [label = " ", linecolor = white, color = white, shape = dots, width = 130, height = 20];
        group hi3-1 {
         label = "Docker";
         color = "#d3d3d3";
         Dummy5 [label = " ", linecolor = white, color = white, shape = dots, width = 130, height = 20];  
           group hi4-1 {
              label = "サービス";
              color = cadetblue;
              I1 -- I2 -- I3 -- I4 -- I5 --I6 -- I7 [color = "#d3d3d3"];
              
           }
        }
        group hi3-2 {
         label = "Vagrant";
         color = "#d3d3d3";
         Dummy6 [label = " ", linecolor = white, color = white, shape = dots, width = 130, height = 20]; 
           group hi4-2 {
              label = "サービス";
              color = cadetblue;
              J1 -- J2 -- J3 -- J4 -- J5 -- J6 [color = "#d3d3d3"];
           }
           
        }
       B -- C -- D -- E [color = "white"];
      }
     
      group hi2-2 {
       label = "開発用 リポジトリサーバ";
       //shape = line;
       color = "#778899";
       F;
      }
      group hi2-3 {
       label = "開発用 課題管理用サーバ";
       //shape = line;
       color = "#778899";
       G;
      }
      group hi2-4 {
       label = "チャットサービス";
       //shape = line;
       color = "#778899";
       H;
      }
     F -- G -- H;
    }
  }


