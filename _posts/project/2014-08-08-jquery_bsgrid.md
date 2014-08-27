--- 
title:      简单易用的jquery grid插件 jquery.bsgrid
layout:     post
permalink:  project/jquery_bsgrid.html
category:   Project
tags: 
 - jQuery
 - Grid
 - bsgrid
---

jquery.bsgrid 简单易用的jquery grid插件
=======================================

<a href="https://github.com/baishui2004/common_gui_tools" target="_blank">jquery bsgrid</a>，A Simple jquery grid plugin with pagation and export. 一个简单易用的jquery grid插件，支持分页或不分页，支持json、xml数据格式，对导出友好，扩展性友好。

当前插件版本：1.11
<br />
文档更新日期：2014-08-26
<br />
在线示例地址：[http://jquery-bsgrid.coding.io/](http://jquery-bsgrid.coding.io/)

###BSGrid的由来###
&emsp;&emsp;首先，澄清插件名称为何叫BSGrid，是因为敝人常用bs开头的字符做英文账号的缘故。BSGrid诞生的原因是主流插件或框架的grid使用或扩展比较复杂。
<br />
以下仅简单说下各插件或框架的grid：
<br />&emsp;&emsp;1，目前主流Grid基本比较适用于内网系统，对于外网系统适用而言，想要改变皮肤样式，字体大小等都非常困难；
<br />&emsp;&emsp;2，主流Grid封装的太好，这反而造成了其扩展性能不是很好，并且其methods、properties很多，上手不容易；
<br />&emsp;&emsp;3，主流grid大多数未提供无分页情况下后台数据的全部展现

###BSGrid的特点###
&emsp;&emsp;1，轻量级，基于jQuery及Html Table，除了对加载数据、分页、渲染数据的简单封装外，不额外增加特别的功能；CSS样式精致简洁，对于扩展修改非常容易；
<br />&emsp;&emsp;2，使用友好，对于一个简单的表格展现，仅仅数十行代码即可完成，并且支持json或xml两种数据格式；且支持友好的导出参数构建；
<br />&emsp;&emsp;3，自带load加载数据遮罩，并很容易进行扩展或重写；
<br />&emsp;&emsp;4，扩展性好，插件有特别好的扩展性，易于对插件本身进行局部甚至较大的修改，易于改变展现样式、渲染数据；插件放开了属性及方法的全局修改权限，所有方法都可在外部进行全局重写，而无需修改插件本身的代码。

###对于主流Grid的简单理解###
大概说下目前的一些主流grid插件或框架的grid
<br />&emsp;&emsp;1，ExtJS，功能丰富，封装好，但属重量级产品，需要加载大体积文件，且响应速度较慢，需商业授权，一般用在内网系统；
<br />&emsp;&emsp;2，DHtmlx，同样功能丰富，封装好，不过其可以根据所需要的模块进行加载，速度方面快于ExtJS，需商业授权，由于其样式不易修改，同样一般用在内网系统；
<br />&emsp;&emsp;3，EasyUI，基于jQuery，语法使用jQuery，却部分地方像ExtJS的写法，在不需其源码的情况下无需商业授权，因无源码而不方便按需模块化加载，也很难改变皮肤样式；
<br />&emsp;&emsp;4，jQGrid，基于jQuery，开源免费且功能特别强大，但同样其样式不易修改；
<br />&emsp;&emsp;5，Flexigrid，基于jQuery，功能逊色，但轻量级，methods、properties较少，不失为想用ExtJS、EasyUI却难以上手这两者的另外一个选择。

###BSGrid示例目录###
<pre>
1，Example Index
2，Simple Grid
3，Simple zh-CN Grid
4，Simple XML Data Grid
5，No Pagation
6，No Diaplay Blank Rows
7，No Data
8，Grid With Checkbox
9，Grid With Little Paging
10，Standard Grid
11，Multi Grid
12，Export Grid
13，Grid with ArtDialog
14，Grid And Form with ArtDialog
</pre>
<!-- more -->

#####1，Example Index#####
![Example Index](https://raw.githubusercontent.com/baishui2004/jquery.bsgrid/master/WebContent/documention/images/jquery.bsgrid-01_examples_index.png)

#####2，Simple Grid#####
![Simple Grid](https://raw.githubusercontent.com/baishui2004/jquery.bsgrid/master/WebContent/documention/images/jquery.bsgrid-02_simple_grid.png)
<pre>
引用文件：
    &lt;link rel="stylesheet" href="../../sources/css/grid.css"/&gt;
    &lt;script type="text/javascript" src="../../plugins/jquery-1.4.4.min.js"&gt;&lt;/script&gt;
    &lt;script type="text/javascript" src="../../sources/js/common.js"&gt;&lt;/script&gt;
    &lt;script type="text/javascript" src="../../sources/js/lang/grid.en.js"&gt;&lt;/script&gt;
    &lt;script type="text/javascript" src="../../sources/js/grid.js"&gt;&lt;/script&gt;
实现代码：
    &lt;table id="searchTable" class="bsgrid"&gt;
        &lt;tr&gt;
            &lt;th w_index="XH" width="5%;"&gt;XH&lt;/th&gt;
            &lt;th w_index="ID" width="5%;"&gt;ID&lt;/th&gt;
            &lt;th w_index="CHAR" w_align="left" w_tip="true" width="15%;"&gt;CHAR&lt;/th&gt;
            &lt;th w_index="TEXT" w_align="left" w_length="50" width="30%;"&gt;TEXT&lt;/th&gt;
            &lt;th w_index="DATE" width="15%;"&gt;DATE&lt;/th&gt;
            &lt;th w_index="TIME" width="15%;"&gt;TIME&lt;/th&gt;
            &lt;th w_index="NUM" width="5%;"&gt;NUM&lt;/th&gt;
            &lt;th w_render="operate" width="10%;"&gt;Operate&lt;/th&gt;
        &lt;/tr&gt;
    &lt;/table&gt;
    &lt;script type="text/javascript"&gt;
        $(function () {
            $.fn.bsgrid.init('searchTable', {
                url: 'data/simple.json',
                // autoLoad: false,
                pageSizeSelect: true,
                pageSize: 10
            });
        });
    
        function operate(record, rowIndex, colIndex, options) {
            return '&lt;a href="#" onclick="alert(\'ID=' + record['ID'] + '\');"&gt;Operate&lt;/a&gt;';
        }
    &lt;/script&gt;
</pre>

#####3，Simple zh-CN Grid#####
![Simple zh-CN Grid](https://raw.githubusercontent.com/baishui2004/jquery.bsgrid/master/WebContent/documention/images/jquery.bsgrid-03_simple_zh-CN_grid.png)
<pre>
1，插件语言本地化文件：grid.en.js、grid.zh-CN.js、grid.zh-TW.js

2，行间隔色配置：stripeRows: true

3，行hover样式：添加如下样式
   /* row hover */
   .bsgrid tr:hover {
        background-color: #ffe48d;
   }
</pre>

#####4，Simple XML Data Grid#####
![Simple XML Data Grid](https://raw.githubusercontent.com/baishui2004/jquery.bsgrid/master/WebContent/documention/images/jquery.bsgrid-04_simple_XML_data_grid.png)
<pre>
默认的是json格式，换加载XML格式数据：
方式1，全局修改加载数据格式：
　　$.fn.bsgrid.defaults.dataType = 'xml';
方式2，单grid修改加载数据格式：
　　$.fn.bsgrid.init('searchTable', {
            url: 'data/simple.xml',
            dataType: 'xml',
            pageSizeSelect: true,
            pageSize: 10
　　});
</pre>

#####5，No Pagation#####
支持展示后台的全部数据，分页工具条变为如下只显示总数的样式：
<br />
![No Pagation](https://raw.githubusercontent.com/baishui2004/jquery.bsgrid/master/WebContent/documention/images/jquery.bsgrid-05_no_pagation.png)
<pre>
实现代码：将pageAll设置为true即可，后台数据格式与分页后台数据格式一致
   $.fn.bsgrid.init('searchTable', {
       url: 'data/simple.json',
       pageAll: true
   });
</pre>

#####6，No Diaplay Blank Rows#####
设置是否显示无数据的行，下图示例展示的是分页行大小是25，但只显示了20条数据，无数据行没有显示：
<br />
![No Diaplay Blank Rows](https://raw.githubusercontent.com/baishui2004/jquery.bsgrid/master/WebContent/documention/images/jquery.bsgrid-06_no_diaplay_blank_rows.png)
<pre>
实现代码：修改全局参数displayBlankRows，默认值为true
　　$.fn.bsgrid.defaults.displayBlankRows = false;
</pre>

#####7，No Data#####
无数据时的提示：
<br />
![No Data](https://raw.githubusercontent.com/baishui2004/jquery.bsgrid/master/WebContent/documention/images/jquery.bsgrid-07_no_data.png)
<pre>
注意此提示仅当$.fn.bsgrid.defaults.displayBlankRows = false;时才会显示，为true时显示的是空行。
说明：属性displayPagingToolbarOnlyMultiPages与displayBlankRows互不影响。
</pre>

#####8，Grid With Checkbox#####
BSGrid内置并不支持checkbox的直接配置，通过column列的w_render属性实现：
<br />
![Grid With Checkbox](https://raw.githubusercontent.com/baishui2004/jquery.bsgrid/master/WebContent/documention/images/jquery.bsgrid-08_grid_with_checkbox.png)
<pre>
实现代码：主要部分
   &lt;th w_render="checkbox" width="3%;"&gt;&lt;input type="checkbox"/&gt;&lt;/th&gt;

   $('#searchTable tr:first th:first input[type=checkbox]').change(function () {
       if ($(this).attr('checked')) {
           $('#searchTable tr:not(:first) td input[type=checkbox]').attr('checked', true);
       } else {
           $('#searchTable tr:not(:first) td input[type=checkbox]').attr('checked', false);
       }
   });

   function checkbox(record, rowIndex, colIndex, options) {
       return '&lt;input type="checkbox" value="' + record['ID'] + '"/&gt;';
   }

   function getCheckedIds() {
       var ids = '';
       $('#searchTable tr:not(:first) td input:checked').each(function () {
           ids += ',' + $(this).val();
       });
       alert(ids.length > 0 ? ids.substring(1) : '');
   }
</pre>

#####9，Grid With Little Paging#####
似ExtJS、EasyUI类分页工具条：
<br />
![Grid With Little Paging](https://raw.githubusercontent.com/baishui2004/jquery.bsgrid/master/WebContent/documention/images/jquery.bsgrid-09_grid_with_little_paging.png)
<pre>
额外引入以下两个文件即可（注意引用顺序），这两个文件是对内置工具条的重写，简单的数几十行代码，充分体现了可扩展性特别强：
   &lt;link rel="stylesheet" href="../../sources/css/grid.paging.little.css"/&gt;
   &lt;script type="text/javascript" src="../../sources/js/grid.paging.little.js"&gt;&lt;/script&gt;
</pre>

#####10，Standard Grid#####
演示BSGrid的大部分对外调用方法，并描述主要配置属性及其作用。
<br />
此处为了演示分页，后台使用jsp页面模拟分页数据，可以完整的展示排序，分页。
<br />
![Standard Grid](https://raw.githubusercontent.com/baishui2004/jquery.bsgrid/master/WebContent/documention/images/jquery.bsgrid-10_standard_grid.png)
<pre>
</pre>

#####11，Multi Grid#####
支持一个页面多grid：
<br />
![Multi Grid](https://raw.githubusercontent.com/baishui2004/jquery.bsgrid/master/WebContent/documention/images/jquery.bsgrid-11_multi_grid.png)
<pre>
</pre>

#####12，Export Grid#####
BSGrid并不是提供导出Grid的页面数据功能，而是进行导出参数的组织：
<br />
![Export Grid](https://raw.githubusercontent.com/baishui2004/jquery.bsgrid/master/WebContent/documention/images/jquery.bsgrid-12_export_grid.png)
<pre>
简单的grid导出参数URL类似如下：
http://jquery-bsgrid.coding.io/examples/grid/export.html?exportFileName=Export%2520Example&dataNames=XH%252CID%252CCHAR%252CTEXT%252CDATE%252CTIME%252CNUM&dataIndexs=XH,ID,CHAR,TEXT,DATE,TIME,NUM&dataLengths=50,50,150,300,150,150,50&dataAligns=center,center,left,left,center,center,center&param1=param1&param2=param2

需要额外引用用于导出的JS：
    &lt;script type="text/javascript" src="../../sources/js/export.js"&gt;&lt;/script&gt;

代码实现，如下，静态页面部分仅再需要增加一个导出按钮即可：
    var gridObj;
    $(function () {
        gridObj = $.fn.bsgrid.init('searchTable', {
            url: 'data/simple.json',
            pageSizeSelect: true,
            pageSize: 10
        });
    });

    function doExport() {
        alert('Only test request params, To see it in browser address url.');
        gridObj.options.otherParames = $('#searchForm').serializeArray();
        $.bsgrid_export.doExport($('#searchTable tr th'), gridObj.options.otherParames, {
            url: 'export.html', // only test request params
            exportFileName: 'Export Example',
            colsProperties: {
                width: 120
            },
            colWidthPercentmultiplier: 10 // if set column width N%, then column width will reset N*10, default 14
        });
    }
</pre>

#####13，Grid with ArtDialog#####
结合ArtDialog使用，演示使用artDialog的锁屏遮罩样式以及覆盖JS原生的alert、confirm、prompt方法。
<br />
<b>特别注意：</b>
<br />&emsp;&emsp;JS原生的alert、confirm、prompt方法是阻塞的，而使用artDialog覆盖的alert、confirm、prompt方法是非阻塞的，artDialog覆盖的方法是用回调方式实现阻塞的等待执行代码效果，详细可参看示例：[Pop with ArtDialog](http://jquery-bsgrid.coding.io/examples/artDialog/pop.html)
<br />
![Grid with ArtDialog](https://raw.githubusercontent.com/baishui2004/jquery.bsgrid/master/WebContent/documention/images/jquery.bsgrid-13_grid_with_artDialog.png)
<pre>
需要额外引用的文件：
    &lt;link rel="stylesheet" href="../../plugins/artDialog/skins/blue.css"/&gt;
    &lt;link rel="stylesheet" href="override/artDialog.skins.override.css"/&gt;
    &lt;script type="text/javascript" src="../../plugins/artDialog/jquery.artDialog.min.js"&gt;&lt;/script&gt;
    &lt;script type="text/javascript" src="../../plugins/artDialog/artDialog.plugins.min.js"&gt;&lt;/script&gt;
    &lt;script type="text/javascript" src="override.grid.js"&gt;&lt;/script&gt;
    &lt;script type="text/javascript" src="override/artDialog.plugin.override.en.js"&gt;&lt;/script&gt;
    &lt;script type="text/javascript" src="override/artDialog.plugin.override.js"&gt;&lt;/script&gt;
    &lt;script type="text/javascript" src="override.pop.js"&gt;&lt;/script&gt;

artDialog需要引用的文件：artDialog/skins/blue.css、artDialog/jquery.artDialog.min.js、artDialog/artDialog.plugins.min.js
覆盖bsgrid的锁屏遮罩样式的文件：override.grid.js
覆盖JS原生的alert、confirm、prompt方法的文件：artDialog.skins.override.css、artDialog.plugin.override.en.js、artDialog.plugin.override.js、override.pop.js
</pre>

#####14，Grid And Form with ArtDialog#####
结合ArtDialog使用，可以完成一个很好看的CRUD功能，详细可查看示例及示例源码：
<br />
![Grid with ArtDialog](https://raw.githubusercontent.com/baishui2004/jquery.bsgrid/master/WebContent/documention/images/jquery.bsgrid-14_grid_and_form_with_artDialog.png)
