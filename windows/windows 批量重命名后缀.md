```
get-childItem 'D:\For PS' *.txt | rename-item -newname { $_.name -replace '\.txt','.html' }

```
**此方法是用来將D盤For PS文件夾下的所有的txt文件改爲html文件，即.txt改爲.html**
