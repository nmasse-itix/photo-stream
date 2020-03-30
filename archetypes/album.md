---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
# By default, photos are sorted by filename
sort_by: Name
# But you can sort instead by EXIF date if you prefer
# sort_by: Exif.Date
resources:
# 
# You can set the album cover image by setting the param 'cover: true'
# on a photo.
# 
# - src: 'IMG_1234.jpeg'
#   params:
#     cover: true
#
- src: '**.jpeg'
- src: '**.jpg'
---
