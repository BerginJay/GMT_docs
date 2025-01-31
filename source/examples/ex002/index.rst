绘制地球内部主要界面
====================

:示例贡献者: 田冬冬（作者）、姚家园（修订）

----

在利用地震波研究地球深部结构时，经常需要绘制震相在深度剖面下的射线路径，
同时也需要绘制地球内部的主要界面。

震相的射线路径可以用 `TauP <http://www.seis.sc.edu/taup/>`__ 提供的 ``taup_path``
命令计算得到，然后在极坐标系 ``-JP`` 中绘制。难点在于如何绘制几个主要界面。

本示例将展示如何绘制震中距为30度的 PcP 和 PKiKP 震相的射线路径，
同时绘制地球内的 410、660界面以及 CMB 和 ICB。
脚本中调用 TauP 计算射线路径。
没有安装 TauP 的用户可以直接下载示例射线路径数据 :download:`PKiKP.raypath.gmt` 和 :download:`PcP.raypath.gmt`。

绘图脚本如下：

.. gmtplot:: ex002.sh
    :width: 50%
    :show-code: true

脚本使用了五次 ``basemap`` 命令，分别绘制五个界面：

- 第一次用于绘制地表：``-Byg6371`` 表明要在 Y 方向（极坐标下即 R 方向）以6371为间隔绘制网格线，
  由于地球半径是6371，所以理论上会在R=0和 R=6371 两处绘制网格线。
  ``-BS`` 的作用是只绘制 R=6371 处的网格线，且只绘制网格线而不绘制刻度
- 第二次用于绘制410界面：与前一命令基本相同，唯一的区别是 ``-Byg6371+5961``
  中多了 ``+5961``，其作用是定义网格线的起算点，即此时将在 R=5961（即410界面）处绘制网格线
- 其他同理
