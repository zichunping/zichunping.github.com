---
layout:     post
title:      markdown study
category: blog
description: markdown语法学习 
---
###参考资料
* [Markdown 语法说明](http://wowubuntu.com/markdown/index.html)
* [Markdown 在线语法](http://wlog.cn/soft/why-use-markdown.html)

###代码区块：前面加一个制表符(tab)，或者4个空格<br />

	if ()
	{
		NSLog(@"123");

	}
###分割线
多个\*
*****

###链接
* 使用方括号后紧跟圆括号并插入网址即可，例如
This is [an example](http://example.com/ "Title") inline link.

###强调
一个\*代表斜体，两个\*粗体，三个\*代表粗斜体

**测试一下**
Use the `printf()` function. 

###代码
使用反引号：\`\`包含内容   `NSLog`

##链接
<http://www.baidu.com> 

<table>
    <tr>
      <th>Markdown</th>
      <th>输出html</th>
      <th>预览</th>
    </tr>
    <tr>
      <td>*强调*</td>
      <td>
        &lt;em>强调&lt;/em>
      </td>
      <td>
        <em>强调</em>
      </td>
    </tr>
    <tr class="alternate">
      <td>**粗体**</td>
      <td>&lt;strong>粗体&lt;strong></td>
      <td><strong>粗体<strong></td>
    </tr>
    <tr>
      <td>
        &gt; 引用
      </td>
      <td>
        &lt;blockquote>引用&lt;/blockquote>
      </td>
      <td>
        <blockquote>引用</blockquote>
      </td>
    </tr>
</table>


<h2>链接和图片</h2>

<table>
    <tr>
      <th width="200">Markdown</th>
      <th width="300">输出html</th>
      <th width="200">预览</th>
    </tr>
  <tr>
    <td>[Google](http://google.com)</td>
    <td>&lt;a href="http://google.com" target="_blank"><br>Google&lt;/a></td>
    <td><a href="http://google.com" target="_blank">Google</a></td>
  </tr>
  <tr class="alternate">
    <td>[bingdian@domain.com](bingdian@domain.com)</td>
    <td>&lt;a href="mailto:bingdian@domain.com">bingdian@<br>domain.com&lt;/a></td>
    <td><a href="mailto:bingdian@domain.com">bingdian@domain.com</a></td>
  </tr>
  <tr class="alternate">
    <td>![The 37signals logo](http://www.37signals.com/images/logo-37signals.png)</td>
    <td>&lt;img src="http://www.37signals.com/images/logo-<br>37signals.png" alt="The 37signals logo" /></td>
    <td><img src="http://www.37signals.com/images/logo-37signals.png" alt="The 37signals logo" /></td>
  </tr>
</table>


<h2>标题</h2>

<table>
    <tr>
      <th>Markdown</th>
      <th>输出html</th>
      <th>预览</th>
    </tr>
  <tr>
    <td># 一级标题</td>
    <td>&lt;h1>一级标题&lt;/h1></td>
    <td><h1>一级标题</h1></td>
  </tr>
  <tr>
    <td>## 二级标题</td>
    <td>&lt;h2>二级标题&lt;/h2></td>
    <td><h2>二级标题</h2></td>
  </tr>
  <tr>
    <td>### 三级标题</td>
    <td>&lt;h3>三级标题&lt;/h1></td>
    <td><h3>三级标题</h3></td>
  </tr>
  <tr>
    <td>#### 四级标题</td>
    <td>&lt;h4>四级标题&lt;/h4></td>
    <td><h4>四级标题</h4></td>
  </tr>
  <tr>
    <td>##### 五级标题</td>
    <td>&lt;h5>五级标题&lt;/h5></td>
    <td><h5>五级标题</h5></td>
  </tr>
  <tr>
    <td>###### 六级标题</td>
    <td>&lt;h6>六级标题&lt;/h6></td>
    <td><h6>六级标题</h6></td>
  </tr>
</table>


<h2>列表</h2>

<table>
    <tr>
      <th>Markdown</th>
      <th>输出html</th>
      <th>预览</th>
    </tr>
  <tr>
    <td>
      * 项目<br />
      * 项目<br />
      * 项目<br />
      &nbsp;&nbsp;* 子项目</span><br />
      &nbsp;&nbsp;* 子项目<br />
      * 项目
    </td>
    <td>
      &lt;ul><br/>
        &nbsp;&nbsp;&lt;li>项目&lt;/li><br/>       
        &nbsp;&nbsp;&lt;li>项目&lt;/li><br/>
        &nbsp;&nbsp;&lt;li>项目<br/>
          &nbsp;&nbsp;&nbsp;&nbsp;&lt;ul><br/>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;li>子项目&lt;/li><br/>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;li>子项目&lt;/li><br/>
          &nbsp;&nbsp;&nbsp;&nbsp;&lt;/ul><br/>
        &nbsp;&nbsp;&lt;/li><br/>
        &nbsp;&nbsp;&lt;li>项目&lt;/li><br/>
      &lt;/ul>
    </td>
    <td>
      <ul>
        <li>项目</li>
        <li>项目</li>
        <li>项目
          <ul>
            <li>子项目</li>
            <li>子项目</li>
          </ul>
        </li>
        <li>项目</li>
      </ul>
    </td>

  </tr>
  <tr class="alternate">
    <td>
      1. 项目<br />
      2. 项目<br />
      3. 项目<br />
      &nbsp;&nbsp;1. 子项目</span><br />
      &nbsp;&nbsp;2. 子项目<br />
      4. 项目
    </td>
    <td>
      &lt;ol><br/>
        &nbsp;&nbsp;&lt;li>项目&lt;/li><br/>
        &nbsp;&nbsp;&lt;li>项目&lt;/li><br/>
        &nbsp;&nbsp;&lt;li>项目<br/>
          &nbsp;&nbsp;&nbsp;&nbsp;&lt;ol><br/>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;li>子项目&lt;/li><br/>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;li>子项目&lt;/li><br/>
          &nbsp;&nbsp;&nbsp;&nbsp;&lt;/ol><br/>
        &nbsp;&nbsp;&lt;/li><br/>
        &nbsp;&nbsp;&lt;li>项目&lt;/li><br/>
      &lt;/ol>
    </td>
    <td>
      <ol>
        <li>项目</li>
        <li>项目</li>
        <li>项目
          <ol>
            <li>子项目</li>
            <li>子项目</li>
          </ol>
        </li>
        <li>项目</li>
      </ol>
    </td>
  </tr>
</table>


<h2>下划线和特殊符号</h2>

<table>
    <tr>
      <th>Markdown</th>
      <th>输出html</th>
      <th>预览</th>
    </tr>
  <tr>
    <td>
      你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线<br />
      ---
    </td>
    <td>
      &lt;hr />
    </td>
    <td>
      <hr />
    </td>
  </tr>
  <tr class="alternate">
    <td>可以利用反斜杠来插入一些在语法中有其它意义的符号<br />
        \*Hi\*
    </td>
    <td>*Hi*</td>
    <td>*Hi*</td>
  </tr>
</table>


<h2>表格</h2>

<p>Markdown：</p>

<pre><code>| First Header  | Second Header |
| ------------- | ------------- |
| Row 1 Cell 1  | Row 1 Cell 2  |
| Row 2 Cell 1  | Row 2 Cell 2  |
</code></pre>


<p>预览：</p>

<table>
<thead>
<tr>
<th> First Header  </th>
<th> Second Header </th>
</tr>
</thead>
<tbody>
<tr>
<td> Row 1 Cell 1  </td>
<td> Row 1 Cell 2  </td>
</tr>
<tr>
<td> Row 2 Cell 1  </td>
<td> Row 2 Cell 2  </td>
</tr>
</tbody>
</table>


<h2>脚注</h2>

<p>Markdown：</p>

<pre><code>Paragraph text with a footnote[^fn]

[^fn]: This is the footnote text.
</code></pre>

<p>预览：</p>

<p>Paragraph text with a footnote<sup id="fnref:1"><a href="#fn:1" rel="footnote">1</a></sup></p>
<div class="footnotes">
<hr/>
<ol>
<li id="fn:1">
<p>This is the footnote text.<a href="#fnref:1" rev="footnote">&#8617;</a></p></li>
</ol>
