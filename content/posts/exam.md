---
title: "Exam"
date: 2021-01-24T19:42:55+08:00
draft: false
---

```python
from django.shortcuts import render
from django.http import HttpResponse
import json

def user(request):
	user_list=['bai','hei']
    return HttpResponse(json.dumps((user_list)))
