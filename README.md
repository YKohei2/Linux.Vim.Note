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


Vim文字化け対策

~/.vimrc (このファイルを作成して下記を記載)

##################################
# Vim起動時に、判別の優先度を定める設定
##################################

# ファイルを読み込む時の、文字コード自動判別の順番
:set fileencodings=utf-8,cp932,euc-jp,sjis


##################################
# Vim起動時に、強制する設定
##################################

# vimの内部文字コード　（これを書くと、上記の優先度設定が無視されます）
:set encoding=utf-8

# ファイルのエンコーディング（改行コードの種類）
:set fileformat=unix

--------------------------------------
cron (ジョブを定期実行する機能)
1. $ sudo su -
2. # systemctl status crond.service (cronのステータス確認)
(止まっている場合 # systemctl start crond.serviceで開始) 
3. # crontab -l (現在のcronの登録されているjob確認)
4. # crontab -e (cronファイルの作成)
5. cat で内容確認
6. # cat /var/log/cron | tail -15 (最後の15行のcronのログを確認する) 


# cat /etc/crontab(cronの設定ファイルの確認)
SHELL=/bin/bash (cronで使用されるシェル)
PATH=/sbin:/bin:/usr/sbin:/usr/bin (PATHの確認, ここが通ってなかったらフルPATHを指定)
MAILTO=root (メールを送る先。ただデータが大きくなりすぎて、サーバがダウンするので設定しない　MAILTO=""でメールを送信しない）



*/1 * * * * date >> /tmp/a.txt
→ 毎分実行



cronの書き方
例:
1  4  10  9  *    date >> /tmp/a.txt
分 時 日  月 曜日 コマンド
 
43 23 * * * date
→23:43に実行

0,10,20,30,40,50 * * * * date
→ 10分おきに実行

*/10 * * * * date
→ 10分おきに実行

* 1 * * * date 
→ 1:00から1:59まで1分おきに実行

0 1 * * * date 
→ 1:00に１回実行

0 */1 * * * date
→ 毎時0分に１時間おきに実行

0 * * * * date
→ 毎時0分に１時間おきに実行




