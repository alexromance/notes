```
get-childItem 'D:\For PS' *.txt | rename-item -newname { $_.name -replace '\.txt','.html' }

```
**此方法是用来將D盤For PS文件夾下的所有的txt文件改爲html文件，即.txt改爲.html**
```language
get-childItem  *.h264 | rename-item -newname { $_.name -replace '\.h264','.mp4' }
```
**此方法是用来将当前所有的h264文件改爲mp4文件，即.h264改爲.mp4**

