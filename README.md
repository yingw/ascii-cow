# 制作自己的IMAGE-COW和定制COW

## 

### ascii-cow
git clone https://github.com/andrewmacheret/ascii-cow.git
### cowsay原版
git clone https://github.com/tnalpgge/rank-amateur-cowsay.git
### im2a
git clone https://github.com/tzvetkoff/im2a.git

基于rank-amateur-cowsay，改名为cowsay
mv rank-amateur-cowsay cowsay

新加定制的cow

ascii-cow/cows/arawana.cow

```txt
##
## A cow with a arawana, from yinguowei@cn.wilmar-intl.com
##
$the_cow = <<EOC;
               $thoughts |
                $thoughts|
     |\\\\\\\\_________
 /=_/            o \\ <_
 |=_           (   v/
 |/ \\__________+___/   (R)
     |///    |/|/
EOC
```
（有点小问题，\、$thoughts在最后不空格）


```sh
tar -czvf cowsay.tar.gz cowsay

tar -czvf im2a.tar.gz im2a

mkdir node_modules

docker build -t yinguowei/ascii-cow .
docker run --rm -it yinguowei/ascii-cow ./ascii-cow.sh -u "$url" -w 80 -c "-f arawana"

```

输出
```txt
 __________________________________________________________________________________ 
/ MMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMM \
| MMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMM |
| MMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMWKOkkk0NMMMWk:''',o0MN0kkkk0WMMMNx;''',dXMM |
| MMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMKOkkkOXMMMMOc'...,cd0WMMM0o,...;xNMMMMM |
| MMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMXOkkkkKNKOxl;'...,dkc'...:kWMMMMMMMM |
| MMMMMMMMMMMMMMMMMMMMMMMKKNMMNXXWMMMMMMMMMMMMMMMN0kkkkkOXMMXd;....'cOMMMMMMMMMMMM |
| MMMMMMMMMMMMMMMMMMMMMMNxx0MMOxx0MMMMMMMMMMMMMMMMMMWKNMMMMMMMMWkoKMMMMMMMMMMMMMMM |
| MMMMMMMMMMMMMMMMMMMMMMMWWMMM0ddKMMMMMMMWNWMMMWNNWMMMMMMWNNNWMMMMMMMMMMNMMMMMMMMM |
| MMMM0ddOMMkdddkMM0dxWMNdxkMM0dxXMMddxOKKxdx00K0xdxMMMkxkOOxdxNMM0ddKkxxMMMMMMMMM |
| MMMMMkddNKdxkddKWdxXMMNdxkMM0ddXMMxddMMMNddOMMM0ddKMMNMMMWOddOMMKddkMMMMMMMMMMMM |
| MMMMMWxdxxxXMkdxkd0MMMNdxkMM0dd0MMxddMMMWddOMMM0ddKMMKkxXWKddOMMXdd0MMMMMMMMMMMM |
| MMMMMMKxddOMMNxddkMMMMNdxkMM0dd0MMxddMMMWddkMMM0ddKM0dd0MM0ddOMMXddOMMMMMMMMMMMM |
| MMMMMMM000MMMMX00WMMMMW000MMX00KMM000MMMW000MMMK00XMMKOkOKW0kOXMN00KMMMMMMMMMMMM |
| MMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMM |
\ MMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMM /
 ---------------------------------------------------------------------------------- 
               \ |
                \|
     |\\\\_________
 /=_/            o \ <_
 |=_           (   v/
 |/ \__________+___/   (R)
     |///    |/|/

```

提交镜像


```
docker login
docker push yinguowei/ascii-cow
```
[yinguowei/ascii-cow - Docker Hub](https://hub.docker.com/r/yinguowei/ascii-cow/)