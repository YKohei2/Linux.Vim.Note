         ___        ______     ____ _                 _  ___  
        / \ \      / / ___|   / ___| | ___  _   _  __| |/ _ \ 
       / _ \ \ /\ / /\___ \  | |   | |/ _ \| | | |/ _` | (_) |
      / ___ \ V  V /  ___) | | |___| | (_) | |_| | (_| |\__, |
     /_/   \_\_/\_/  |____/   \____|_|\___/ \__,_|\__,_|  /_/ 
 ----------------------------------------------------------------- 


Hi there! Welcome to AWS Cloud9!

To get started, create some files, play with the terminal,
or visit https://docs.aws.amazon.com/console/cloud9/ for our documentation.

Happy coding!
# Linux.Vim.Note

$sudo su - (一時的にrootユーザーで操作する)
$exit (root権限からログアウト)
$cp file2 file3 (file2をコピーしてfile3という名前を付ける)
$cp -p file2 file4 (file4を作ってファイル２と４の更新日を同時にする)
$mv file2 ../test2 (file2を一つ上に戻ってtest2のディレクトリに移動する)
$vi file2 → :q!(vimの編集を保存しないで終了) 
$cat -n file2 (file2の中身を行数込みで表示させる)
$touch testfile{1..10} (testfile1から10（合計10個のファイル)を一度に作る
--------------------------------------
シェルスクリプト
move.sh(ファイル名+.shでシェルスクリプトのファイル作成)
vi で操作内容記載
例:
#!/bin/bash (これは固定で毎回記載する)

echo "テストファイルを移動します"
ls -l testfile*  (*でtestfileと名前のつくファイルがすべて実行対象になる)
mv testfile* ../
echo "テストファイルを移動しました"

./move.sh (シェルスクリプト実行)
----------------------------------

num = 10 (numに10を代入している。)
echo $num (変数を確認)
printenv (全変数を確認できる)
r : 読み取り権限
w : 書き込み権限
x : 実行権限
- : 権限なし

- rwx(所有者の権限)r-x(同グループの権限)r-x(その他の権限) 1 root root

$ chmod 777 file2 (file2の権限をフル権限に変更) 

権限表
1 001 --x
2 010 -w-
3 011 -wx
4 100 r--
5 101 r-x
6 110 rw-
7 111 rwx    


