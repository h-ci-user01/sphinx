###########################
Sphinxの図形描画機能の検討
###########################

blockdiag Pluginを利用したフロー図の描画
=========================================


.. blockdiag::

    blockdiag {
       Start -> Work1 -> Goal;
       Start -> Work2 -> Work3 -> Goal;
    }


標準機能を利用した表の描画
==========================

====== ================
ID      プロジェクト名
====== ================
001      公開
002      管理
====== ================


seqdiag Pluginを利用したシーケンス図の描画
==========================================

.. seqdiag::
   :desctable:

   seqdiag {
      HSE --> GitHub[label = "git push"];
      GitHub -> TravisCI[label = "order CI"]
      GitHub -> Redmine[label = "Ticket update"]
      Redmine -> Slack[label = "send notification"]
      GitHub -> Slack[label = "send notification"]
      TravisCI -> Slack[label = "send notification"]
      Slack --> HSE[label = "check notification"]
      HSE [description = "Hi SE"];
      GitHub [description = "Repository Management System"];
      TravisCI [description = "CI Service"]
      Redmine [description = "Project Management System"];
      Slack [description = "Chat Service"]
   }


