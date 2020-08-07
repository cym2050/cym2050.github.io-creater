---
title: "HTML"
date: 2020-07-31T22:12:44+08:00
draft: true
---

##### HTML:超文本标记语言
1. HTML的版本、HTML 4.01、XTML、HTML5、HTML 5.1
2. 规范文档根据浏览器的实际情况总结，由W3C编写
3. DOCTYPE
用来选择文档类型
4. 常见标签
a、form、input、button、h1、p、ul、ol、small、strong、div、kbd、video、audio、svg，除了div和span，其他标签都有默认样式
5. 什么是空标签
没有闭合的标签称为空标签，如：`<br />`和`<img />`等。 他们不存在成对的情况,反之具有成对性质的例如：`<div></div>、 <form></form> `就不是空标签。在HTML中，在空标签上使用闭标签是无效的，例如： `</br>` 。
6. 什么是可替换标签
在 [CSS](https://developer.mozilla.org/zh-CN/docs/Web/CSS) 中，**可替换元素**（**replaced element**）的展现效果不是由 CSS 来控制的。这些元素是一种外部对象，它们外观的渲染，是独立于 CSS 的。简单来说，它们的内容不受当前文档的样式的影响。CSS 可以影响可替换元素的位置，但不会影响到可替换元素自身的内容。某些可替换元素，例如 [`<iframe>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/iframe "HTML内联框架元素 <iframe> 表示嵌套的浏览上下文，有效地将另一个HTML页面嵌入到当前页面中。") 元素，可能具有自己的样式表，但它们不会继承父文档的样式。
典型的可替换元素有：
*   [`<iframe>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/iframe "HTML内联框架元素 <iframe> 表示嵌套的浏览上下文，有效地将另一个HTML页面嵌入到当前页面中。")
*   [`<video>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/video "HTML <video> 元素 用于在HTML或者XHTML文档中嵌入媒体播放器，用于支持文档内的视频播放。")
*   [`<embed>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/embed "HTML <embed> 元素将外部内容嵌入文档中的指定位置。此内容由外部应用程序或其他交互式内容源（如浏览器插件）提供。")
*   [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img "HTML Image 元素（ <img> ）代表文档中的一个图像。")

7. 学会查看MDN文档

HTML所有标签：
*   [<!DOCTYPE>](https://www.w3school.com.cn/tags/tag_doctype.asp "HTML <!DOCTYPE> 标签")

*   [<a>](https://www.w3school.com.cn/tags/tag_a.asp "HTML <a> 标签")
*   [<abbr>](https://www.w3school.com.cn/tags/tag_abbr.asp "HTML <abbr> 标签")
*   [<acronym>](https://www.w3school.com.cn/tags/tag_acronym.asp "HTML <acronym> 标签")
*   [<address>](https://www.w3school.com.cn/tags/tag_address.asp "HTML <address> 标签")
*   [<applet>](https://www.w3school.com.cn/tags/tag_applet.asp "HTML <applet> 标签")
*   [<area>](https://www.w3school.com.cn/tags/tag_area.asp "HTML <area> 标签")
*   [<article>](https://www.w3school.com.cn/tags/tag_article.asp "HTML <article> 标签")
*   [<aside>](https://www.w3school.com.cn/tags/tag_aside.asp "HTML <aside> 标签")
*   [<audio>](https://www.w3school.com.cn/tags/tag_audio.asp "HTML <audio> 标签")
*   [<b>](https://www.w3school.com.cn/tags/tag_b.asp "HTML <b> 标签")
*   [<base>](https://www.w3school.com.cn/tags/tag_base.asp "HTML <base> 标签")
*   [<basefont>](https://www.w3school.com.cn/tags/tag_basefont.asp "HTML <basefont> 标签")
*   [<bdi>](https://www.w3school.com.cn/tags/tag_bdi.asp "HTML <bdi> 标签")
*   [<bdo>](https://www.w3school.com.cn/tags/tag_bdo.asp "HTML <bdo> 标签")
*   [<big>](https://www.w3school.com.cn/tags/tag_big.asp "HTML <big> 标签")
*   [<blockquote>](https://www.w3school.com.cn/tags/tag_blockquote.asp "HTML <blockquote> 标签")
*   [<body>](https://www.w3school.com.cn/tags/tag_body.asp "HTML <body> 标签")
*   [<br>](https://www.w3school.com.cn/tags/tag_br.asp "HTML <br> 标签")
*   [<button>](https://www.w3school.com.cn/tags/tag_button.asp "HTML <button> 标签")
*   [<canvas>](https://www.w3school.com.cn/tags/tag_canvas.asp "HTML <canvas> 标签")
*   [<caption>](https://www.w3school.com.cn/tags/tag_caption.asp "HTML <caption> 标签")
*   [<center>](https://www.w3school.com.cn/tags/tag_center.asp "HTML <center> 标签")
*   [<cite>](https://www.w3school.com.cn/tags/tag_cite.asp "HTML <cite> 标签")
*   [<code>](https://www.w3school.com.cn/tags/tag_phrase_elements.asp "HTML <code> 标签")
*   [<col>](https://www.w3school.com.cn/tags/tag_col.asp "HTML <col> 标签")
*   [<colgroup>](https://www.w3school.com.cn/tags/tag_colgroup.asp "HTML <colgroup> 标签")
*   [<command>](https://www.w3school.com.cn/tags/tag_command.asp "HTML <command> 标签")
*   [<datalist>](https://www.w3school.com.cn/tags/tag_datalist.asp "HTML <datalist> 标签")
*   [<dd>](https://www.w3school.com.cn/tags/tag_dd.asp "HTML <dd> 标签")
*   [<del>](https://www.w3school.com.cn/tags/tag_del.asp "HTML <del> 标签")
*   [<details>](https://www.w3school.com.cn/tags/tag_details.asp "HTML <details> 标签")
*   [<dfn>](https://www.w3school.com.cn/tags/tag_phrase_elements.asp "HTML <dfn> 标签")
*   [<dialog>](https://www.w3school.com.cn/tags/tag_dialog.asp "HTML <dialog> 标签")
*   [<dir>](https://www.w3school.com.cn/tags/tag_dir.asp "HTML <dir> 标签")
*   [<div>](https://www.w3school.com.cn/tags/tag_div.asp "HTML <div> 标签")
*   [<dl>](https://www.w3school.com.cn/tags/tag_dl.asp "HTML <dl> 标签")
*   [<dt>](https://www.w3school.com.cn/tags/tag_dt.asp "HTML <dt> 标签")
*   [<em>](https://www.w3school.com.cn/tags/tag_phrase_elements.asp "HTML <em> 标签")
*   [<embed>](https://www.w3school.com.cn/tags/tag_embed.asp "HTML <embed> 标签")
*   [<fieldset>](https://www.w3school.com.cn/tags/tag_fieldset.asp "HTML <fieldset> 标签")
*   [<figcaption>](https://www.w3school.com.cn/tags/tag_figcaption.asp "HTML <figcaption> 标签")
*   [<figure>](https://www.w3school.com.cn/tags/tag_figure.asp "HTML <figure> 标签")
*   [<font>](https://www.w3school.com.cn/tags/tag_font.asp "HTML <font> 标签")
*   [<footer>](https://www.w3school.com.cn/tags/tag_footer.asp "HTML <footer> 标签")
*   [<form>](https://www.w3school.com.cn/tags/tag_form.asp "HTML <form> 标签")
*   [<frame>](https://www.w3school.com.cn/tags/tag_frame.asp "HTML <frame> 标签")
*   [<frameset>](https://www.w3school.com.cn/tags/tag_frameset.asp "HTML <frameset> 标签")
*   [<h1> - <h6>](https://www.w3school.com.cn/tags/tag_hn.asp "HTML <h1> - <h6> 标签")
*   [<head>](https://www.w3school.com.cn/tags/tag_head.asp "HTML <head> 标签")
*   [<header>](https://www.w3school.com.cn/tags/tag_header.asp "HTML <header> 标签")
*   [<html>](https://www.w3school.com.cn/tags/tag_html.asp "HTML <html> 标签")
*   [<i>](https://www.w3school.com.cn/tags/tag_i.asp "HTML <i> 标签")
*   [<iframe>](https://www.w3school.com.cn/tags/tag_iframe.asp "HTML <iframe> 标签")
*   [<img>](https://www.w3school.com.cn/tags/tag_img.asp "HTML <img> 标签")
*   [<input>](https://www.w3school.com.cn/tags/tag_input.asp "HTML <input> 标签")
*   [<ins>](https://www.w3school.com.cn/tags/tag_ins.asp "HTML <ins> 标签")
*   [<kbd>](https://www.w3school.com.cn/tags/tag_phrase_elements.asp "HTML <kbd> 标签")
*   [<keygen>](https://www.w3school.com.cn/tags/tag_keygen.asp "HTML <keygen> 标签")
*   [<label>](https://www.w3school.com.cn/tags/tag_label.asp "HTML <label> 标签")
*   [<legend>](https://www.w3school.com.cn/tags/tag_legend.asp "HTML <legend> 标签")
*   [<li>](https://www.w3school.com.cn/tags/tag_li.asp "HTML <li> 标签")
*   [<link>](https://www.w3school.com.cn/tags/tag_link.asp "HTML <link> 标签")
*   [<main>](https://www.w3school.com.cn/tags/tag_main.asp "HTML <main> 标签")
*   [<map>](https://www.w3school.com.cn/tags/tag_map.asp "HTML <map> 标签")
*   [<mark>](https://www.w3school.com.cn/tags/tag_mark.asp "HTML <mark> 标签")
*   [<menu>](https://www.w3school.com.cn/tags/tag_menu.asp "HTML <menu> 标签")
*   [<menuitem>](https://www.w3school.com.cn/tags/tag_menuitem.asp "HTML <menuitem> 标签")
*   [<meta>](https://www.w3school.com.cn/tags/tag_meta.asp "HTML <meta> 标签")
*   [<meter>](https://www.w3school.com.cn/tags/tag_meter.asp "HTML <meter> 标签")
*   [<nav>](https://www.w3school.com.cn/tags/tag_nav.asp "HTML <nav> 标签")
*   [<noframes>](https://www.w3school.com.cn/tags/tag_noframes.asp "HTML <noframes> 标签")
*   [<noscript>](https://www.w3school.com.cn/tags/tag_noscript.asp "HTML <noscript> 标签")
*   [<object>](https://www.w3school.com.cn/tags/tag_object.asp "HTML <object> 标签")
*   [<ol>](https://www.w3school.com.cn/tags/tag_ol.asp "HTML <ol> 标签")
*   [<optgroup>](https://www.w3school.com.cn/tags/tag_optgroup.asp "HTML <optgroup> 标签")
*   [<option>](https://www.w3school.com.cn/tags/tag_option.asp "HTML <option> 标签")
*   [<output>](https://www.w3school.com.cn/tags/tag_output.asp "HTML <output> 标签")
*   [<p>](https://www.w3school.com.cn/tags/tag_p.asp "HTML <p> 标签")
*   [<param>](https://www.w3school.com.cn/tags/tag_param.asp "HTML <param> 标签")
*   [<pre>](https://www.w3school.com.cn/tags/tag_pre.asp "HTML <pre> 标签")
*   [<progress>](https://www.w3school.com.cn/tags/tag_progress.asp "HTML <progress> 标签")
*   [<q>](https://www.w3school.com.cn/tags/tag_q.asp "HTML <q> 标签")
*   [<rp>](https://www.w3school.com.cn/tags/tag_rp.asp "HTML <rp> 标签")
*   [<rt>](https://www.w3school.com.cn/tags/tag_rt.asp "HTML <rt> 标签")
*   [<ruby>](https://www.w3school.com.cn/tags/tag_ruby.asp "HTML <ruby> 标签")
*   [<s>](https://www.w3school.com.cn/tags/tag_s.asp "HTML <s> 标签")
*   [<samp>](https://www.w3school.com.cn/tags/tag_phrase_elements.asp "HTML <samp> 标签")
*   [<script>](https://www.w3school.com.cn/tags/tag_script.asp "HTML <script> 标签")
*   [<section>](https://www.w3school.com.cn/tags/tag_section.asp "HTML <section> 标签")
*   [<select>](https://www.w3school.com.cn/tags/tag_select.asp "HTML <select> 标签")
*   [<small>](https://www.w3school.com.cn/tags/tag_small.asp "HTML <small> 标签")
*   [<source>](https://www.w3school.com.cn/tags/tag_source.asp "HTML <source> 标签")
*   [<span>](https://www.w3school.com.cn/tags/tag_span.asp "HTML <span> 标签")
*   [<strike>](https://www.w3school.com.cn/tags/tag_strike.asp "HTML <strike> 标签")
*   [<strong>](https://www.w3school.com.cn/tags/tag_phrase_elements.asp "HTML <strong> 标签")
*   [<style>](https://www.w3school.com.cn/tags/tag_style.asp "HTML <style> 标签")
*   [<sub>](https://www.w3school.com.cn/tags/tag_sub.asp "HTML <sub> 标签")
*   [<summary>](https://www.w3school.com.cn/tags/tag_summary.asp "HTML <summary> 标签")
*   [<sup>](https://www.w3school.com.cn/tags/tag_sup.asp "HTML <sup> 标签")
*   [<table>](https://www.w3school.com.cn/tags/tag_table.asp "HTML <table> 标签")
*   [<tbody>](https://www.w3school.com.cn/tags/tag_tbody.asp "HTML <tbody> 标签")
*   [<td>](https://www.w3school.com.cn/tags/tag_td.asp "HTML <td> 标签")
*   [<textarea>](https://www.w3school.com.cn/tags/tag_textarea.asp "HTML <textarea> 标签")
*   [<tfoot>](https://www.w3school.com.cn/tags/tag_tfoot.asp "HTML <tfoot> 标签")
*   [<th>](https://www.w3school.com.cn/tags/tag_th.asp "HTML <th> 标签")
*   [<thead>](https://www.w3school.com.cn/tags/tag_thead.asp "HTML <thead> 标签")
*   [<time>](https://www.w3school.com.cn/tags/tag_time.asp "HTML <time> 标签")
*   [<title>](https://www.w3school.com.cn/tags/tag_title.asp "HTML <title> 标签")
*   [<tr>](https://www.w3school.com.cn/tags/tag_tr.asp "HTML <tr> 标签")
*   [<track>](https://www.w3school.com.cn/tags/tag_track.asp "HTML <track> 标签")
*   [<tt>](https://www.w3school.com.cn/tags/tag_tt.asp "HTML <tt> 标签")
*   [<u>](https://www.w3school.com.cn/tags/tag_u.asp "HTML <u> 标签")
*   [<ul>](https://www.w3school.com.cn/tags/tag_ul.asp "HTML <ul> 标签")
*   [<var>](https://www.w3school.com.cn/tags/tag_phrase_elements.asp "HTML <var> 标签")
*   [<video>](https://www.w3school.com.cn/tags/tag_video.asp "HTML <video> 标签")
*   [<wbr>](https://www.w3school.com.cn/tags/tag_wbr.asp "HTML <wbr> 标签")