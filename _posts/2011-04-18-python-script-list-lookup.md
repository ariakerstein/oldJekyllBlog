---
id: 1560
title: 'Python script: list lookup'
date: 2011-04-18T06:10:18+00:00
author: arisamuel
type: posts
layout: single
guid: http://www.directedattention.com/?p=1560
permalink: /python-script-list-lookup/
original_post_id:
  - "1560"
categories:
  - python
  - scripts
  - Uncategorized
tags:
  - python
  - scripts
---
<pre>Here is a very simple, very useful script to lookup a value in a list of lists.<br />
[sourcecode language="python"]</p>


<p>
  # Define a procedure, lookup,<br />
  # that takes two inputs:<br />
  # - an index<br />
  # - keyword
</p>


<p>
  # The procedure should return a list<br />
  # of the urls associated<br />
  # with the keyword. If the keyword<br />
  # is not in the index, the procedure<br />
  # should return an empty list.
</p>


<p>
  index = [['corewheels', ['http://corewheelfitness.com', 'http://www.akrowheels.com']],<br />
           ['computing', ['http://acm.org']]]
</p>


<p>
  def lookup(index,keyword):<br />
      for entry in index:<br />
          if entry[0]==keyword:<br />
              return entry[1]<br />
          return []
</p>


<p>
  print lookup(index,'corewheels')<br />
  #>>> ['http://corewheelfitness.com', 'http://www.akrowheels.com']<br />
  [/sourcecode]
</p>