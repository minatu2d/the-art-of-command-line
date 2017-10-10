🌍
*[Čeština](README-cs.md) ∙ [Deutsch](README-de.md) ∙ [Ελληνικά](README-el.md) ∙ [English](README.md) ∙ [Español](README-es.md) ∙ [Français](README-fr.md) ∙ [Indonesia](README-id.md) ∙ [Italiano](README-it.md) ∙ [日本語](README-ja.md) ∙ [한국어](README-ko.md) ∙ [Português](README-pt.md) ∙ [Română](README-ro.md) ∙ [Русский](README-ru.md) ∙ [Slovenščina](README-sl.md) ∙ [Українська](README-uk.md) ∙ [简体中文](README-zh.md) ∙ [繁體中文](README-zh-Hant.md)∙ [Tiếng Việt](README-vi.md)*


# Nghệ thuật sử dụng dòng lênh 

[![Ask a Question](https://img.shields.io/badge/%3f-Ask%20a%20Question-ff69b4.svg)](https://airtable.com/shrzMhx00YiIVAWJg)

[![Join the chat at https://gitter.im/jlevy/the-art-of-command-line](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/jlevy/the-art-of-command-line?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)


- [Một số điều cần nói trước](#meta)
- [Cơ bản](#basics)
- [Sử dụng hàng ngày](#everyday-use)
- [Xử lý file (tệp) và dữ liệu](#processing-files-and-data)
- [ Debug (Gỡ rối) hệ thống](#system-debugging)
- [ Xử lý một dong - One-liners](#one-liners)
- [Ít còn phổ biến nhưng vẫn hữu dụng](#obscure-but-useful)
- [Chỉ dành OS X](#os-x-only)
- [Chỉ dành Windows](#windows-only)
- [Các nguồn khác](#more-resources)
- [Disclaimer](#disclaimer)


![curl -s 'https://raw.githubusercontent.com/jlevy/the-art-of-command-line/master/README.md' | egrep -o '`\w+`' | tr -d '`' | cowsay -W50](cowsay.png)

Thành thạo việc sử dụng dòng lệnh là một kĩ năng thường bị xem nhẹ hoặc được xem như một dạng bí quyết, nhưng thực sự nó giúp cải thiện tính linh hoạt và năng xuất làm việc cho engineer một cách rõ ràng và tinh tế. Đây là một  đống các notes và tips (mẹo) hữu ích, được lựa chọn trong quá trình sử dụng dòng lệnh trên Linux. Một vài tips thì khá cơ bản, một số lại tương đối đặc trưng, phức tạp, hoặc có thể đã không còn phổ biến nữa. Trang này sẽ không dài đâu, nhưng nếu bạn có thể sử dụng và lặp lại những cái được nói đến ở đây, bạn cũng biết khá nhiều rồi đấy.

Nội dung này là kết quả của rất nhiều tác giả và người dịch [many authors and translators](AUTHORS.md).
Một vài thông tin:
[ban đầu](http://www.quora.com/What-are-some-lesser-known-but-useful-Unix-commands)
[tiếp đến](http://www.quora.com/What-are-the-most-useful-Swiss-army-knife-one-liners-on-Unix)
trên [Quora](http://www.quora.com/What-are-some-time-saving-tips-that-every-Linux-user-should-know),
 nhưng nó đã được đưa lên GitHub, nơi có rất nhiều người tài năng hơn cả chính tác giả ban đầu đã đóng góp cho nó.
[**Hãy đặt một câu hỏi**](https://airtable.com/shrzMhx00YiIVAWJg) nếu bạn có bất cứ thắc mắc nào liên quan đến các câu lệnh trong bài. [**Hãy đóng góp**](/CONTRIBUTING.md) nếu bạn thấy có lỗi hoặc có gì đó có thể tốt hơn!

## Một số điều cần nói trước

Phạm vi bài viết:

- Hướng dẫn này dành cho cả người bắt đầu và người đã có kinh nghiệm. Mục tiêu hướng đến là *tính bao phủ rộng* (tất cả những thứ quan trọng), *tính cụ thể* (đưa ví dụ cụ thể trong hầu hết các trường hợp phổ biến), and *tính ngắn gọn* (tránh những thứ không thực sự là thiết, ít được sử dụng hoặc cái mà bạn có thể dễ dàng tìm được ở những chỗ khác). Mỗi tip đều được coi là cần thiết trong một số tình huống hoặc tiết kiệm thời gian một cách đáng kể so với những cái khác.
- Chỉ viết chạy trên Linux, trừ các chương "[ Chỉ dành cho](#os-x-only)" và "[Windows only](#windows-only)" . Rất nhiều cái khác có thể được áp dụng hoặc cài đặt trên cái hệ thống Unices khác hoặc OS X (thậm chí Cygwin).
- Tập trung xoanh quanh Bash ở chế động tương tác, mặc dù nhiều tips có thể được áp dụng trên các shells khác nhưng về cơ bản là hướng đến Bash scripting.
- Nó sẽ bao gồm cả câu lệnh Unix "chuẩn" cũng như những câu lệnh cần cài đặt gói đặc biệt -- miễn là nó đủ quan trọng để cho được nói đến.

Chú ý:

- Để giữ nội dung chỉ trong 1 trang, nội dung được ngầm định có cả ở trong các tham khảo nữa. Bạn đủ khả năng để tìm hiểu chi tiết một khi biết ý tưởng hoặc câu lệnh để hỏi Google. Sử dụng `apt-get`, `yum`, `dnf`, `pacman`, `pip` hoặc `brew` (khi thích hợp) để cài đặt.
- Sử dụng [Explainshell](http://explainshell.com/) để có được thông tin chi tiết xem dòng lệnh này làm cái gì, các option, rồi pipelines etc. do.


## Cơ bản 

- Học cơ bản về Bash. Thực ra, chỉ cần gõ `man bash` và xem qua ít nhất một lượt; nó rất dễ để theo dõi và cũng không quá dài. Các shell khác có thể ngon hơn ở một số điểm, nhưng Bash rất mạnh mẽ và đặc biệt luôn được cài sẵn trên nhiều hệ thống (nếu *chỉ* học zsh, fish, etc., ở trên laptop thôi cũng được, nhưng nó khiến cho bạn bị hạn chế trong nhiều tình huống, như trên hầu hết các server đang chạy chẳng hạn).

- Học ít nhất một trình soạn thảo (editor). Lý tưởng nhất là Vim (`vi`), nó thực sự vô đối cho tác vụ soạn thảo ở trên terminal (thậm chí hiện tại nếu bạn đang sử dụng Emacs, rồi thì một IDE khá to, một editor ngầu trong dạo gần gần đây).

- Biết cách đọc tài liệu bằng câu lệnh `man` (nếu tò mò, lệnh `man man` sẽ liệt kê các số section, ví dụ 1 tương ứng với các câu lệnh thuộc loại "phổ biến", 5 là các files/quy ước, và 8 dành cho việc quản trị). Tìm các trang man này bằng `apropos`. Nhớ rằng một vài command không phải chương trình binary tương ứng, mà là có sẵn trong Bash ( hay gọi builtins), và bạn có thể xem trợ giúp của chúng bằng lệnh `help` và `help -d`. Bạn có thể kiểm tra một câu lệnh có chương trình tương ứng, hay có sẵn trong shell hay là một lệnh đại diện (alias) bằng cách sử dụng `type command` với command là câu lệnh muốn kiểm tra.

- Học về chuyển hướng của  output và input sử dụng `>` và `<` rồi thì đường ống (pipes) sử dụng `|` (tên dân dã là gì quên mất rồi, rào hay xoạc gì đó). Nhớ rằng `>` sẽ ghi đè file đầu ra, còn `>>` sẽ thêm vào cuối file. Học về để biết stdout, stderr.

- Học về mở rộng ra danh sách file (file glob expansion) cho kí hiệu `*` (hoặc `?` và cả `[`...`]` nữa), rồi thì phân biệt giữa bao bằng nháy kép `"` và nháy đơn `'`. (Xem thêm về mở rộng giá trị biến ở bên dưới.)

- Làm quen với quản lý job trong Bash thông qua: `&`, **ctrl-z**, **ctrl-c**, `jobs`, `fg`, `bg`, `kill`, etc.

- Biết về `ssh`, và các phương pháp xác thực không password, thông qua `ssh-agent`, `ssh-add`, etc.

- Cơ bản về quản lý file: `ls` and `ls -l` ( cụ thể hơn, là biết về ý nghĩa mỗi cột trong danh sách mà `ls -l` đưa ra), `less`, `head`, giữa `tail` và `tail -f` (hoặc thậm chí tốt hơn nữa hơn nữa là `less +F`), giữa `ln` và `ln -s` (học về sự khác nhau cũng như lợi ích giữa liên kết cứng (hard link) và liên kết mềm (soft link)), `chown`, `chmod`, `du` (cho việc kiểm tra nhanh tình trạng sử dụng thiết bị lưu trữ: `du -hs *`). Để quản lý hệ thống file sử dụng `df`, `mount`, `fdisk`, `mkfs`, `lsblk`. Học để biết inode là cái gì ( rồi ý nghĩa đầu ra của `ls -i` hoặc `df -i`).

- Quản lý mạng cơ bản: `ip` hoặc `ifconfig`, `dig`, `traceroute`, `route`.

- Học và sử dụng một hệ thống quản lý phiên bản (Version Control System), như `git` chẳng hạn.

- Hiểu rõ biểu thức chính quy, và nhiều cờ khác nhau cho `grep`/`egrep`. Như `-i`, `-o`, `-v`, `-A`, `-B`, và `-C` là các options nên biết.

- Học cách sử dụng `apt-get`, `yum`, `dnf` hoặc `pacman` (phụ thuộc vào bản phân phối bạn đang sử dụng) để tìm và cài đặt gói cần thiết. Và chắc rằng bạn có `pip` để cài đặt các câu lệnh viết bằng Python (một vài lệnh dưới đây được cài đặt dễ dàng nhất qua `pip`).


## Sử dụng hàng ngày 

- Trong Bash, sử dụng **Tab** hoàn thành tham số, liệt kê các câu lệnh dùng với đoạn đang gõ, dùng **ctrl-r** để tìm kiếm trong lịch sử các câu lệnh đã chạy (sau khi gõ được một đoạn, nhấn **ctrl-r** nhiều lần để xem lệnh kết quả tìm kiếm trong lịch sử, nhấn **Enter** để chạy lệnh đã tìm được, hoặc nhấn nút mũi tên sang phải để chính sửa lệnh đang tìm được).

- Trong Bash, sử dụng **ctrl-w** để xóa từ (word) cuối cùng, và **ctrl-u** để xóa nội dung từ con trỏ trở về đầu dòng. Sử dụng **alt-b** và **alt-f** để di chuyển về trước (b - backward) hoặc về sau (f - forward) một từ, **ctrl-a** để di chuyển con trỏ về đầu dòng,  **ctrl-e** để di chuyển con trỏ về cuối, **ctrl-k** để xóa từ vị trí con trỏ đến cuối dòng, **ctrl-l** để xóa màn hình, đưa dòng lệnh về góc trên trái. Mở `man readline` để xem tất cả các phím tắt mặc định trong Bash. Có rất rất nhiều khó mà nhớ hết được. Ví dụ, **alt-.** để tham số cuối của lần lượt các câu lệnh trước ngay trước đó, và **alt-*** để mở rộng glob (tức là thay thế các kí tự wildcard như `*` ngay lập tức).


- Ngoài ra, nếu bạn thích các phím tắt theo phong cách của `vi` thì có thể thiết lập `set -o vi` (và sử dụng `set -o emacs` để quay lại mặc định).

- Để gõ những câu lệnh dài tránh, bạn có thể thiết lập một editor (ví dụ bằng lệnh `export EDITOR=vim`), sau đó sử dụng tổ hợp phím **ctrl-x** **ctrl-e**, nó sẽ mở câu lệnh đang gõ trong editor được thiết lập đó, cho phép dễ dàng edit hơn ở chế độ nhiều dòng. Hoặc chỉnh sửa bằng vi luôn, sử dụng phím **escape-v**.

- Để xem danh sách câu lệnh đã chạy, sử dụng `history`. Sử dụng `!n` (với `n` là chỉ số của câu lệnh trong bảng mà `history` đưa ra) để chạy lại câu lệnh tương ứng. Cũng có rất nhiều dạng viết tắt khác bạn có thể sử dụng với các câu lệnh lịch sử, hữu ích nhất có lẽ là `!$` để lấy tham số cuối cùng của câu lệnh chạy ngay trước và `!!` gọi lại chính câu lệnh trước (xem thêm phần "HISTORY EXPANSION"  trong trang manunal của lệnh `history`). Thực tế thì, viết tắt này có thể dễ dàng thay thế bằng cách kết hợp **ctrl-r** (tìm trong danh sách lệnh đã chạy) và **alt-.** (mở rộng các glob).

- Trở về thư mục home bằng `cd` (không tham số). Sử dụng `~` để đại diện cho thư mục home của user hiện tại (ví dụ `~/.bashrc`). Đường dẫn thư mục home là giá trị biến môi trường `$HOME` luôn.

- Trở về thư mục ngay trước khi chuyển đến thư mục hiện tại: `cd -`.

- Lúc bạn đang gõ một câu lệnh mà thấy phân vân, không muốn thực hiện nói nữa, hãy gõ **alt-#** ngay lập tức dòng đó sẽ được thêm `#` và trở thành một dòng comment (gõ lần lượt **ctrl-a**, **#**, **enter** cũng có tác dụng tương tự). Dù comment thì vẫn được lưu lại trong history, bạn có thể gọi lại nó.

- Sử dụng`xargs` (hoặc `parallel`). Nó rất rất mạnh. Chú ý là, bạn có thể làm việc với nhiều trường dữ liệu trên 1 dòng (`-L`) cũng như song song (`-P`). Nếu bạn không chắc về câu lệnh được thực hiện trong `args` có đúng hay không, đầu tiên hãy sử dụng `xargs echo` để kiểm tra các tham số đã. Rồi thì, `-I{}` cũng rất tiện dụng. Như ví sau:
```bash
      find . -name '*.py' | xargs grep some_function
      cat hosts | xargs -I{} ssh root@{} hostname
```

- `pstree -p` để hiển thị các process đang chạy theo dạng cây.

- Sử dụng `pgrep` và `pkill` để tìm process rồi thì gửi `signal` (tín hiệu, yêu cầu) đến process theo tên tên của chúng (`-f` sẽ hữu ích).

- Biết nhiều loại tín hiệu có thể gửi cho process. Ví dụ, để dừng một process, sử dụng `kill -STOP [pid]`. Để xem danh sách đầy đủ của các tín hiệu này, xem ở `man 7 signal`

- Sử dụng `nohup` hoặc `disown` nếu bạn muốn tiến trình chạy nền chạy mãi mà không bị tắt khi tắt terminal.

- Kiểm tra process nào đang lắng nghe mạng bằng `netstat -lntp` hoặc `ss -plat` (mặc định là TCP; thêm `-u` cho UDP) hoặc `lsof -iTCP -sTCP:LISTEN -P -n` (chạy cả trên cả OS X).

- Có cả `lsof` và `fuser` kiểm tra xem có socket và file nào đang mở.

- Dùng `uptime` hoặc `w` để biết hệ thống đã chạy bao lâu chưa tắt.

- Sử dụng `alias` để tạo một tên khác cho các câu lệnh hay sử dụng. Ví dụ, `alias ll='ls -latr'` sẽ tạo một `câu lệnh mới` có tên là `ll`.

- Các `alias`, các thiết lập shell, các hàm hay sử dụng nên được lưu vào `~/.bashrc`, rồi [thứ tự các file được source khi login vào shell](http://superuser.com/a/183980/7106). Sử dụng những cái này giúp bạn thiết lập cho mỗi phiên làm việc trên shell của bạn.

- Đặt các thiết lập biến môi trường cũng như các câu lệnh cần chạy lúc đăng nhập ở file `~/.bash_profile`. Tách riêng các cấu hình khi sử dụng cho các shell được khởi động từ môi trường đồ họa hoặc liên quan `cron`.

- Đồng bộ các file cấu hình (e.g. `.bashrc` and `.bash_profile`) giữa nhiều máy bằng Git.

- Hiểu rằng cần chú ý đến giá trị biến hoặc tên file mà chứa khoảng trắng. Nên đặt biến khi được sử dụng trong cặp dấu nháy kém, ví dụ: `"$FOO"`. Ưu tiên sử dụng `-0` hoặc `-print0` để cho phép khoảng kí tự null làm kí tự ngăn cách các tên file, ví dụ: `locate -0 pattern | xargs -0 ls -al` or `find / -print0 -type d | xargs -0 ls -al`. Rồi thì trước khi xem từng tên file trong một danh sách file (có tên file chứa khoảng trắng) bằng vòng lặp, hãy gán biến IFS để chỉ cho phép sử dụng kí tự phân cách là new line (kí tự xuống dòng) mà thôi, `IFS=$'\n'`.

- Trong Bash script, sử dụng `set -x` (hoặc là `set -v`, khi đó nó sẽ ghi lại - logs lại các đầu vào của script, cả các biến chưa được mở rộng, rồi cả comment nữa) cho mục đích debug. Hãy sử dụng chế độ nghiêm khắc (strict mode) trừ khi bạn có lý do đủ hợp lý để không sử dụng nó, mode này bao gồm các thiết lập sau đây. Sử dụng `set -e` để dừng lại khi gặp lỗi (kết thúc bất cứ chỗ nào mà giá trị trả về khác 0). Sử dụng `set -u` để phát hiện việc sử dụng các biến chưa được gán lần nào trước khi sử dụng. Xem xét sử dụng cả `set -o pipefail` nữa, nhằm xử lý các lỗi liên quan đến pipeline (nhớ hãy đọc thêm cho kĩ nếu định sử dụng nó, ở đây chỉ giới thiệu một chút vậy thôi). Khi có nhiều script liên quan, cũng có thể sử dụng `trap` khi xảy EXIT hoặc ERR (lỗi). Một thói quen khá là tốt là nên bắt đầu script bằng đoạn như sau, mục đích là sẽ phát hiện và dừng script, in lỗi khi gặp các lỗi phổ biến:
```bash
      set -euo pipefail
      trap "echo 'error: Script failed: see failed command above'" ERR
```

- Trong Bash script, các shell con - subshelll (được viết trong dấu ngoặc đơn) là một cách khá tiện để nhóm các câu lệnh lại với nhau. Ví dụ phổ biến là, thực hiện câu lệnh ở thư mục khác rồi quay lại thư mục ban đầu, như dưới đây: 
```bash
      # do something in current dir
      (cd /some/other/dir && other-command)
      # continue in original dir
```

- Trong Bash, có rất nhiều kiểu mở rộng biến (tức là thay biến bằng giá trị thật ở lúc chạy). Kiểm tra một biến có tồn tại hay không sử dụng: `${name:?error message}`. Ví dụ, nếu một script Bash chỉ yêu cầu một tham số đầu vào, ta có thể viết đơn giản như sau `input_file=${1:?usage: $0 input_file}`. Sử dụng một giá trị mặc định nếu biến là rỗng: `${name:-default}`. Nếu bạn có thêm nhiều tham số hơn nữa, bạn có thể sử dụng kiểu như này `output_file=${2:-logfile}`. Nếu `$2` không được truyền vào ( tứ là rỗng), `output_file` sẽ được gán là `logfile`. Các phép mở rộng số học: `i=$(( (i + 1) % 5 ))`. Dãy số: `{1..10}`. Cắt gọt chuỗi: `${var%suffix}` và `${var#prefix}`. Ví dụ nếu `var=foo.pdf`, thì câu lệnh `echo ${var%.pdf}.txt` sẽ in ra `foo.txt`.

- Rút gọn cách viết sử dụng `{`...`}` có thể giảm việc phải gõ cũng như tự động được phần kết hợp các đoạn với nhau. Cái này rất hữu ích khi sử dụng với câu lệnh dạng `mv foo.{txt,pdf} some-dir` (di chuyển cả 2 file trong 1 câu lệnh), `cp somefile{,.bak}` (cái mà sẽ được mở rộng thành `cp somefile somefile.bak`) hoặc `mkdir -p test-{a,b,c}/subtest-{1,2,3}` (sẽ mở rộng thành tất cả các dạng kết hợp có thể rồi tạo cây thư mục).

- Đầu ra của một câu lệnh có thể được sử dụng như là một file bằng theo cách `<(some command)`. Ví dụ, so sánh file `/etc/hosts` ở local với file đó trên remote:
```sh
      diff /etc/hosts <(ssh somehost cat /etc/hosts)
```

- Khi viết script, bạn có thể đặt code bên trong một cặp ngoặc móc. Nếu việc đóng mở không chính xác, script của bạn sẽ không thể chạy được do mắc lỗi cú pháp (syntax error). Cái này khá hợp lý khi script của bạn được download từ web về, cái này sẽ chống lại việc chỉ một phần của script đó được chạy:
```bash
{
      # Your code here
}
```

- Biết về cái (nội dung ở đây) hay  "here documents" trong Bash, tức là `cat <<EOF ...` sau đó nhập cần truyền cho `cat`.

- Trong Bash, chuyển hướng cả đầu ra chuẩn (stdout) và đầu ra thông báo lỗi (stderr) thì sử dụng: `some-command >logfile 2>&1` hoặc `some-command &>logfile`. Thông thường, để đảm bảo rằng câu lệnh không thể nhận gì từ đầu vào chuẩn, nó có thể là bất cứ thứ gì bạn gõ vào terminal đang sử dụng, hãy thêm vào `</dev/null`.

- Sử dụng `man ascii` để xem bảng ASCII, cùng với giá trị hex, dec của nó. Về thông tin chung liên quan đến encoding, sử dụng `man unicode`, `man utf-8`, và `man latin1` cũng rất hữu ích.

- Sử dụng `screen` hoặc [`tmux`](https://tmux.github.io/) để tạo ra nhiều của sổ làm việc, đặc biệt hữu ích khi làm việc với session trên remote host, các công cụ này cho phép detach (tách), retach (gắn lại) session. `byobu` có thể nâng cao hơn cho screen hoặc tmux qua để cung cấp thông tin và dễ quản lý hơn. Một tiện ích cực nhỏ khác dành riêng cho việc quản lý các session là  [`dtach`](https://github.com/bogner/dtach).

- Trong ssh, biết làm thế nào để tạo một tunnel (đường ống) bằng tham số `-L` or `-D` (thỉnh thoảng còn cả `-R`) là rất có ích, ví dụ truy cập web site thông qua một remote server.

- Một vài tối ưu cho cấu hình ssh của bạn cũng có thể hữu ích; ví dụ, file `~/.ssh/config` chứa những thiết lập để tránh đứt kết nối trong một vài môi trường mạng cụ thể, sử dụng nén - compress ( cái cũng sẽ giúp ích khi sử dụng scp với kết nối có băng thông thấp - low-bandwidth connections), đa kênh - multiplex channels đến cũng một server bằng file thiết lập ở local:
```
      TCPKeepAlive=yes
      ServerAliveInterval=15
      ServerAliveCountMax=6
      Compression=yes
      ControlMaster auto
      ControlPath /tmp/%r@%h:%p
      ControlPersist yes
```

- Một vài options sử dụng cho ssh như liên quan đến security nên được bật một cách cẩn trọng, ví dụ, cho mỗi subnet hoặc host hoặc trong các mạng tin cậy được - trusted networks: `StrictHostKeyChecking=no`, `ForwardAgent=yes`

- Xem xét sử dụng [`mosh`](https://mosh.mit.edu/) như là một giải pháp thay thế ssh, cái mà sử dụng UDP, tránh việc bị ngắt kết nối, cũng như những tính năng tiện dụng khác ( cần phải thiết lập cả phía server-side nữa).

- Để xem quyền - permission trên một file ở dạng cơ số 8, cái thông tin thường xuyên xuất hiện trong thiết lập hệ thống nhưng lại không hiện ra ở trong câu lệnh `ls` và dễ dàng bị bối rối, sử dụng câu lệnh sau để giải quyết nó: 
```sh
      stat -c '%A %a %n' /etc/timezone
```

- Dành cho việc tương tác với đầu ra của một câu lệnh khác, sử dụng [`percol`](https://github.com/mooz/percol) hoặc [`fzf`](https://github.com/junegunn/fzf).

- Dành cho việc thao tác với các file từ đầu ra của một câu lệnh khác (như `git`), sử dụng `fpp` ([PathPicker](https://github.com/facebook/PathPicker)).

- Một web server đơn giản cho phép xem, tải các file ở thư mục hiện tại (cả các thư mục con nữa), có thể truy cập trên tất cả các mạng mà máy đang kết nối, use:
`python -m SimpleHTTPServer 7777` ( sử dụng cổng port 7777 trên Python 2) và `python -m http.server 7777` ( sử dụng cổng 7777 trên Python 3).

- Chạy một câu lệnh với tư các là một user khác, sử dụng `sudo`. Nếu không chỉ ra thì mặc định sẽ là root; Thêm tham số `-u` để chỉ rõ user. Sử dụng `-i` để đăng nhập vào user đó (bạn sẽ được hỏi để nhập _your_ password).

- Để chuyển sang shell cho một user khác, sử dụng `su username` hoặc `su - username`. Dấu "-" sẽ lấy môi trường như user đó đang login. Nếu không có tham số user thì mặc định sẽ là root. Bạn sẽ được hỏi password _user mà định chuyển sang_.

- Biết về giới hạn 128K - [128K limit](https://wiki.debian.org/CommonErrorMessages/ArgumentListTooLong) trong dòng lệnh. Cái lỗi "Argument list too long" khá phổ biến giá trị wilcard được mở rộng ra quá nhiều file, nhất là với `ls`. (khi xảy ra lỗi này, sử dụng các lệnh khác như `find` và `xargs` có thể giải quyết được.)

- Cho các thao tác tính toán trên máy tính bỏ túi ( đơn giản là truy cập vào Python), sử dụng trình thông dịch của  `python`. Ví dụ,
```
>>> 2+3
5
```


## Xử lý files và dữ liệu 

- Để tìm file theo tên trong thư mục hiện tại, sử dụng `find . -iname '*something*'` (hoặc tương tự). Để tìm một file theo tên ở mọi nơi có thể, sử dụng `locate something` (những phải nhớ rằng `updatedb` có thể chưa index các file mới có gần đây).

- Để tìm kiếm nội dung file mã nguồn rồi data, có một vài options cải tiến và tốt hơn `grep -r`, bao gồm (theo thứ tự từ cũ đến mới) [`ack`](https://github.com/beyondgrep/ack2), [`ag`](https://github.com/ggreer/the_silver_searcher) ("the silver searcher"), và [`rg`](https://github.com/beyondgrep/ack2) (ripgrep).

- Để chuyển từ HTML sang text: `lynx -dump -stdin`

- Để xem dạng Markdown, HTML, hay các dạng chuyển đổi định dạng tài liệu khác, hãy thử [`pandoc`](http://pandoc.org/).

- Nếu bạn muốn theo tác với XML, `xmlstarlet` vẫn tốt dù khá cũ.

- Với JSON, sử dụng [`jq`](http://stedolan.github.io/jq/).

- Với YAML, sử dụng [`shyaml`](https://github.com/0k/shyaml).

- Cho Excel hoặc CSV files, [csvkit](https://github.com/onyxfish/csvkit) cung cấp các lệnh `in2csv`, `csvcut`, `csvjoin`, `csvgrep`, etc.

- Cho Amazon S3, [`s3cmd`](https://github.com/s3tools/s3cmd) khá tiện lơi và [`s4cmd`](https://github.com/bloomreach/s4cmd) thì nhanh hơn. Amazon's [`aws`](https://github.com/aws/aws-cli) và phiển bản cải tiến [`saws`](https://github.com/donnemartin/saws) là khá cơ bản cho các task vụ liên quan đến AWS.

- Biết về `sort` và `uniq`, bao gồm các tham số của uniq như `-u` và `-d` -- xem phần one-liners bên dưới. Cả phần nữa `comm`.

- Biết về `cut`, `paste`, và `join` để thao tác với file text. Rất nhiều người sử dụng `cut` nhưng ít khi nhớ đến `join`.

- Biết về `wc` để đếm dòng (`-l`), kí tự (`-m`), từ (`-w`) và cả số bytes nữa (`-c`).

- Biết về `tee`, nó thực hiện copy stdin ra file, đồng thời in ra cả stdout nữa, như trong lệnh sau chẳng hạn `ls -al | tee file.txt`.

- Với những tính toán phức tạp hơn, bao gồm nhóm, đảo thứ tự các trường, các phép toán thống kê, hãy xem xét [`datamash`](https://www.gnu.org/software/datamash/).

- Biết thông tin địa lý, quốc gia - locale có ảnh hưởng đến rất nhiều câu lệnh theo nhiều cách rất khó để ý, bao gồm thứ tự sắp xếp (sự đối chiếu - hay sự so sánh) vả cả hiệu năng (performace). Hồi hết bản cài đặt Linux sẽ thiết lập `LANG` hoặc các biến môi trường liên quan đến địa lý khác thành thiết lập cục bộ như dạng US English. Nhưng phải nhận thức rằng việc sắp xếp (thứ tự sắp xếp) có thể thay đổi nếu thay đổi thông tin địa lý - locale. Và biết về các đoạn xử lý i18n có thể khiến cho lênh sắp xếp và một số lệnh khác chạy chậm hơn rất *nhiều lần*. Trong một vài tình huống, ( như các thao tác thiết lập hoặc các thao tác duy nhất ở dưới đây) bạn có thể tránh các đoạn xử lý liên quan đến i18n và sử dụng các thao tác sắp xếp dựa trên byte, bằng cách gán `export LC_ALL=C`.

- Bạn có thể thực hiện một câu lệnh trong điều kiện nhất định của biến môi trường, như câu lệnh sau: `TZ=Pacific/Fiji date`.

- Biết cơ bản về `awk` và `sed` cho các thao tác dữ liệu đơn giản. Xem [One-liners](#one-liners) để biết thêm ví dụ.

- Để thay thế trong tất cả các chỗ tìm thấy được trong một hoặc nhiều file:
```sh
      perl -pi.bak -e 's/old-string/new-string/g' my-files-*.txt
```

- Để đổi tên nhiều file hoặc/và tìm kiếm/thay thế trong  file, hãy thử [`repren`](https://github.com/jlevy/repren). ( Trong nhiều trường hợp, lệnh `rename` cũng có thể thực hiện đổi tên nhiều file được, nhưng hãy cẩn thận vì chức năng này không giống nhau trên tất cả các bản phân phối Linux.)
```sh
      # Thay đổi toàn bộ từ tên file, các thư mục, và cả nội dụng từ: foo -> bar:
      repren --full --preserve-case --from foo --to bar .
      # Recover các file đã backup whatever.bak -> whatever:
      repren --renames --from '(.*)\.bak' --to '\1' *.bak
      # Giống câu lệnh ngay trên, nhưng sử dụng rename nếu nó có sẵn:
      rename 's/\.bak$//' *.bak
```

- Trong man page của `rsync` có nói, `rsync` thực sự là một công cụ sao chép nhanh fast và cực kì linh hoạt. Nó vấn được xem là công cụ để đồng bộ giữa các máy với nhau, những cũng hưu ích không kém khi sử dụng trong 1 máy. Khi bị hạn chế bởi các quy định về securities, việc sử dụng `rsync` thay cho `scp` cho phép phục hồi lại quá trình truyền file mà không cần làm lại từ đầu. Nó cũng là một trong những cách nhanh nhất [fastest ways](https://web.archive.org/web/20130929001850/http://linuxnote.net/jianingy/en/linux/a-fast-way-to-remove-huge-number-of-files.html) để xóa một lượng lớn file:
```sh
mkdir empty && rsync -r --delete empty/ some-dir && rmdir some-dir
```

- Để xem tiến trình hoàn thành (progress) khi sao chép, sử dụng `pv`, [`pycp`](https://github.com/dmerejkowsky/pycp), [`progress`](https://github.com/Xfennec/progress), `rsync --progress`, hoặc, ở sao chép ở mức độ block-level,  sử dụng `dd status=progress`.

- Sử dụng `shuf` để xáo trộn hoặc chọn một dòng bất kì từ file.

- Biết các option của `sort`. Với sắp xếp số, sử dụng `-n`, hoặc `-h` để hiển thị dạng số mà con người có thể hiểu - human-readable ( ví dụ `du -h` chẳng hạn). Biết keys hoạt động ra sao (`-t` and `-k`). Cụ thể, bạn cần viết  `-k1,1` để sắp xếp chỉ trường kí tự đầu tiên; `-k1` có nghĩa là sắp xếp theo toàn bộ dòng. Sắp xếp ổn định (`sort -s`) có thể hữu ích. Ví dụ, đầu tiên sắp xếp bằng trường thứ 2, sau đó sắp xếp bằng trường thứ nhất, bạn có thể sử dụng `sort -k1,1 | sort -s -k2,2`.

- Nếu bạn muốn viết kí tự tab trong dòng lệnh của Bash ( ví dụ cho tham số -t cho sort), nhấn **ctrl-v** **[Tab]** hoặc viết `$'\t'` (cách sau tốt hơn vì bạn có thể copy/past chúng).

- Công cụ chuẩn cho việc patching - thực thi sửa đổi trên mã nguồn là `diff` và `patch`. Có nên tham khảo `diffstat` để xem các thông tin kết quả tổng quan, diff và `sdiff` để xem trực quan sự khác nhau (màn hình được chia đôi). Chú ý rằng `diff -r` sẽ áp dụng cho toàn bộ thư mục. Sử dụng `diff -r tree1 tree2 | diffstat` để xem sự khác nhau giữa 2 cây thư mục. Sử dụng `vimdiff` để so sánh và chỉnh sửa file file.

- Với các file nhị phân, sử dụng `hd`, `hexdump` hoặc `xxd` cho các tham tác xem nội dung đơn giản, và `bvi`, `hexedit` hoặc `biew` để chỉnh sửa nội dung binary .

- Cũng cho file nhị phân, `strings` ( thêm `grep`, etc.) cho phép tìm một chuỗi từ dữ liệu binary.

- Để so sánh file nhị phân (delta compression), sử dụng `xdelta3`.

- Để chuyển đổi encoding của kí tự, thử sử dụng `iconv`. Hoặc `uconv` cho nâng cao hơn; vì nó hỗ trợ một vài thứ nâng cao liên quan đến Unicode. Ví dụ, sẽ thực hiện đổi về chữ thường và bỏ hết các accents ( bằng cách mở rộng hoặc bỏ chúng):
```sh
      uconv -f utf-8 -t utf-8 -x '::Any-Lower; ::Any-NFD; [:Nonspacing Mark:] >; ::Any-NFC; ' < input.txt > output.txt
```

- Để chia file thành nhiều file nhỏ, xem lệnh `split` ( để chia theo kích thước) và `csplit` (để chia theo mẫu - pattern).

- Để thao tác với date và các biểu thức thời gian, sử dụng `dateadd`, `datediff`, `strptime` etc. từ công cụ [`dateutils`](http://www.fresse.org/dateutils/).

- Sử dụng `zless`, `zmore`, `zcat`, và `zgrep` để thao tác với các file nén - compressed file.

- Các thuộc tính file có thể được set bằng `chattr` và cho phép truy cập các permission liên quan đến file ở mức thấp nữa. Ví dụ, để bảo việc các file tránh bị xóa nhầm, một cờ cần được bật:  `sudo chattr +i /critical/directory/or/file`

- Sử dụng `getfacl` và `setfacl` để lưu lại và phục hồi quyền liên quan đến file (file permission). Ví dụ:
```sh
   getfacl -R /some/path > permissions.txt
   setfacl --restore=permissions.txt
```

- Để tạo một file rỗng nhanh chóng, sử dụng `truncate` ( tạo [sparse file](https://en.wikipedia.org/wiki/Sparse_file)), `fallocate` (ext4, xfs, btrfs and ocfs2 filesystems), `xfs_mkfile` ( với hầu hết hệ thống file, có trong gói xfsprogs), `mkfile` (cho các hệ thống file giống Unix-like như Solaris, Mac OS).

## Debug hệ thống 

- Để debug web, `curl` và `curl -I` rất tiện, `wget` cũng tương tự, hoặc hiện đại hơn là [`httpie`](https://github.com/jkbrzt/httpie).

- Để biết tình trạng sử dụng hiện tại của cpu/disk, tool truyền thống là `top` (hoặc tốt hơn nữa là `htop`), `iostat`, và `iotop`. Sử dụng `iostat -mxz 15` cho thông tin cơ bản về CPU và thông tin chi tiết trên mỗi phân vùng của đĩa, rồi thì cái nhìn tổng quan liên quan đến hiệu năng.

- Thông tin chi tiết của kết nối mạng, use `netstat` and `ss`.

- Một cái nhìn nhanh về cái gì đang xảy ra trên hệ thống, thì `dstat` đặc biệt hữu ích. Muốn xem cái nhìn chi tiết và rộng nhất, sử dụng [`glances`](https://github.com/nicolargo/glances).

- Để biết trạng thái của bộ nhớ, chạy cũng như hiểu đầu ra của các lệnh như `free` và `vmstat`. Cụ thể, hiểu rõ giá trị "cached" là bộ nhớ được giữ bởi nhân Linux kernel như cache cho file, vì thế có thể tính vào giá trị "free"  được.

- Debug chương trình viết bằng Java thì lại là một cái khác hẳn, nhưng có một mẹo đơn giản khi sử dụng máy ảo Oracle và một vài máy ảo JVMs là bạn có thể chạy `kill -3 <pid>`, và các thông tin đầy đủ về stack trace, bộ nhớ heap (bao gồm thông tin chi tiết về cả bộ dọn rác, đó thực sự là thông tin rất hưu dụng) sẽ được xuất ra - dump stderr/logs. Các lệnh có sẵn của  JDK như `jps`, `jstat`, `jstack`, `jmap` cũng hữu ích. [SJK tools](https://github.com/aragozin/jvm-tools) là một công cụ nâng cao hơn.

- Sử dụng [`mtr`](http://www.bitwizard.nl/mtr/) là công cụ để traceroute tốt hơn, rồi thì xác định vấn đề của mạng.

- Để tìm hiểu tại sao đĩa cứng lại đầy, [`ncdu`](https://dev.yorhel.nl/ncdu) là tiết kiệm thời gian nhất so với câu lệnh thông thường `du -sh *`.

- Để tìm xem cái socket hay process nào đang sử dụng bandwidth, sử dụng [`iftop`](http://www.ex-parrot.com/~pdw/iftop/) hoặc [`nethogs`](https://github.com/raboof/nethogs).

- Cộng cụ tên `ab` (đền từ Apache) sẽ hữu ích cho việc kiểm tra nhanh tuy không kĩ (quick-and-dirty) performance của web server. Để kiểm tra tải phức tạp hơn , hãy thử `siege`.

- Để debug mạng một cách nghiêm túc, sử dụng [`wireshark`](https://wireshark.org/), [`tshark`](https://www.wireshark.org/docs/wsug_html_chunked/AppToolstshark.html), hoặc [`ngrep`](http://ngrep.sourceforge.net/).

- Biết cách sử dụng `strace` và `ltrace`. Các công cụ này sẽ hữu dụng khi chương trình của bạn đang bị lỗi, bị treo (hanging), hoặc tắt đột ngột (crashing), mà bạn không biết tại sao, hoặc bạn muốn tìm ý tưởng để nâng cao performance. Hãy chú ý đến cái option để profiling (`-c`), rồi thì có thể gắn vào một process đang chạy (`-p`). Sử dụng (`-f`) để trace cả những tiến trình con nhằm tránh bị lỡ những lời gọi quan trọng.

- Biết về `ldd` để kiểm tra các thư viện động được sử dụng trong một file chạy — nhưng đừng bao giờ chạy nó với một file mà chưa được tin tưởng như bài viết sau [never run it on untrusted files](http://www.catonmat.net/blog/ldd-arbitrary-code-execution/).

- Biết cách để kết nối gdb vào một tiên trình đang chạy và lấy stack trace của nó.

- Sử dụng `/proc`. Nó thỉnh thoảng sẽ rất hữu ích khi debugging vấn đề một cách `live`. Ví dụ: `/proc/cpuinfo`, `/proc/meminfo`, `/proc/cmdline`, `/proc/xxx/cwd`, `/proc/xxx/exe`, `/proc/xxx/fd/`, `/proc/xxx/smaps` ( ở đây `xxx` process id hay pid).

- Khi debug những bị sai đã xảy ra rồi, thì [`sar`](http://sebastien.godard.pagesperso-orange.fr/) cực kì hữu ích. Nó chỉ ra cả thông kê có tính lịch sử của CPU, bộ nhớ, mạng, etc.

- Khi muốn phân tích kĩ hơn về hệ thống và performance, hãy xem `stap` ([SystemTap](https://sourceware.org/systemtap/wiki)), [`perf`](https://en.wikipedia.org/wiki/Perf_%28Linux%29), và [`sysdig`](https://github.com/draios/sysdig).

- Kiểm tra thông tin hệ điều hành bạn đang dùng `uname` hoặc `uname -a` (thông tin chung của Unix/kernel) hoặc `lsb_release -a` (thông tin về bản phân phối).

- Sử dụng `dmesg` khi có có gì đó xảy ra một cách "vui tính" ( có thể liên quan đến phần cứng hardware hoặc driver ).

- Nếu bạn xóa một file mà dung lượng nó chiếm giữ vẫn chưa được trả lại trong thông tin lệnh `du`, thì có thể kiểm tra xem file này được sử dụng bởi process nào khác không:
`lsof | grep deleted | grep "filename-of-my-big-file"`


## One-liners - Tác vụ bằng một dòng lệnh

Một vài ví dụ của việc kết hợp các câu lệnh với nhau:

- Nó thực sự hữu ích khi bạn làm việc với các thao tác với tập hợp như phép giao (intersection), phép hợp (union), và các xử lý khác của file text bằng cặp lệnh `sort`/`uniq`. Giả sử `a` và `b` là 2 file text có mà mỗi cái chứa từng dòng khác nhau. Đoạn lệnh dưới đây sẽ hoạt động cực nhanh, làm việc với bất cứ kích thước nào của file, có thể đến hàng GB. ( Thao tác sắp sếp - Sort không bị giới hạn bởi bộ nhớ, bạn cần thêm tham số `-T` nếu `/tmp` nằm trên một phân vùng nhỏ.) Cũng phải để ý đến đoạn nói đến `LC_ALL` ở trên và sắp xếp - `sort` với tham số `-u` (để tạo sự rõ ràng).
```sh
      sort a b | uniq > c   # c is a union b
      sort a b | uniq -d > c   # c is a intersect b
      sort a b b | uniq -u > c   # c is set difference a - b
```

- Sử dụng `grep . *` để xem xét tất nội dung của tất cả các file trong thư mục một cách nhanh chóng (nội dung mỗi dòng được bắt đầu với tên file tương ứng luôn), hoặc `head -100 *` ( mỗi file lấy một đoạn đầu thôi). Cái này hữu ích khi xem các thư mục chứa toàn các thiết lập cấu hình trong đó như `/sys`, `/proc`, `/etc`.


- Tổng tất cả các số trong cột thứ 3 của một file text ( cách này dường như nhanh hơn 3X và ít code hơn 3X lần so đoạn code Python tương ứng để làm việc này):
```sh
      awk '{ x += $3 } END { print x }' myfile
```

- Để xem kích thước/ngày giờ trên một cây thư mục, files, cái này sẽ thực hiện xoáy sâu xuống `ls -l` có thể dễ đọc hơn nếu sử dụng `ls -lR`:
```sh
      find . -type f -ls
```

- Bạn có một file text, giống như log của web server chẳng hạn, và có một giá trị nhất định chỉ xuất hiện ở vài dòng thôi, như tham số `acct_id` xuất hiện trong URL chẳng hạn. Nếu bạn muốn đếm xem có bao nhiêu yêu cầu cho mỗi `acct_id`:
```sh
      egrep -o 'acct_id=[0-9]+' access.log | cut -d= -f2 | sort | uniq -c | sort -rn
```

- Để theo dõi thay đổi một cách liên tục, sử dụng `watch`, ví dụ, để kiểm tra thay đổi thay đổi của các file trong một thư mục chẳng hạn, sử dụng `watch -d -n 2 'ls -rtlh | tail'` hoặc theo dõi trạng thái mạng khi đang xem xét vấn đề liên quan đến thiết lập wifi chẳng hạn, sử dụng `watch -d -n 2 ifconfig`.

- Chạy hàm sau đây để lấy và hiển thị một tip bất kì từ tài liệu này (đọc Markdown và lấy các item trong đó):
```sh
      function taocl() {
        curl -s https://raw.githubusercontent.com/jlevy/the-art-of-command-line/master/README.md |
          pandoc -f markdown -t html |
          xmlstarlet fo --html --dropdtd |
          xmlstarlet sel -t -v "(html/body/ul/li[count(p)>0])[$RANDOM mod last()+1]" |
          xmlstarlet unesc | fmt -80
      }
```


## Ít còn phổ biến nhưng vẫn hữu ích 

- `expr`: thực hiện phép tính toán toán học hoặc logic hoặc đánh giá biểu thức chính quy. 

- `m4`: một trình xử lý macro đơn giản 

- `yes`: In một chuỗi nhiều lần 

- `cal`: một cái lịch khá đẹp 

- `env`: chạy một câu lệnh (hữu dụng khi viết scripts)

- `printenv`: in ra các biến môi trường (hữu dụng khi debug và viết script)

- `look`: tìm từ tiếng Anh - English words ( hoặc các dòng trong file) thông qua từ bắt đầu 

- `cut`, `paste` and `join`: thao tác với dữ liệu 

- `fmt`: định dạng đoạn văn bản 

- `pr`: định dạng văn bản theo hàng và cột 

- `fold`: hiển thị dòng text trên nhiều dòng màn hình 

- `column`: Định dạng các trường được tách thành các cột có kích thước cố định hoặc bảng 

- `expand` và `unexpand`: chuyển đổi giữa tab và space 

- `nl`: thêm số dòng 

- `seq`: in ra số, hữu ích khi tạo dãy số liên tiếp

- `bc`: máy tính bỏ túi 

- `factor`: phân tích nguyên tố 

- [`gpg`](https://gnupg.org/): mã hóa và thực hiện ghi chữ kí cho dữ liệu

- `toe`: bảng chứa tất cả các loại terminal cùng thông tin của nó 

- `nc`: debug mạng và truyền dữ liệu 

- `socat`: chuyển socket và forward cổng tcp ( tương tự `netcat`)

- [`slurm`](https://github.com/mattthias/slurm): công cụ xem traffic mạng 

- `dd`: di chuyển dữ liệu giữa các file hoặc thiết bị

- `file`: xác định loại file 

- `tree`: hiển thị thư mục cùng với thư mục on của nó ở dạng cây; giống với `ls` có đi sâu xuống

- `stat`: thông tin file 

- `time`: thực hiện và tính thời gian thực hiện một câu lệnh 

- `timeout`: thực hiện câu lệnh trong một khoảng thời gian nhất định, dừng tiến trình khi đến khoảng thời gian đó mà câu lệnh vẫn chưa hoàn thành.

- `lockfile`: tạo một file semaphore chỉ có thể được xóa bởi `rm -f`

- `logrotate`: xoay vòng, nén and gửi mail log.

- `watch`: chạy một đoạn lệnh lặp đi lặp lại, hiển thị kết quả, hoặc/và làm nổi bật thay đổi

- [`when-changed`](https://github.com/joh/when-changed): chạy một câu lệnh được chỉ định bất cứ khi nào thấy có sự thay đổi trên file. Xem thêm cả `inotifywait` và `entr`.

- `tac`: In nội dung file theo thức tự ngược lại 

- `shuf`: chọn vài dòng ngẫu nhiên từ file 

- `comm`: so sánh file theo dạng dòng với dòng 

- `strings`: tách chuỗi từ một file binary 

- `tr`: chuyển đổi và thao tác với chuỗi kí tự 

- `iconv` hoặc `uconv`: chuyển đổi encoding 

- `split` và `csplit`: chia file 

- `sponge`: đọc toàn bộ đầu vào rồi mới ghi chúng ra đầu ra, hữu dụng khi đọc và ghi từ/đến cùng một file, ví dụ ., `grep -v something some-file | sponge some-file`

- `units`: chuyển đổi đơn vị và tính toán; từ số ngày trong tuần đến số twip trên một nhấp nháy ( xem thêm ở `/usr/share/units/definitions.units`)

- `apg`: sinh một password ngẫu nhiên

- `xz`: nén file tỉ lệ nén cao 

- `ldd`: kiểm tra thông tin thư viện động 

- `nm`: lấy thông tin các symbol (hàm, biến public) trong file

- `ab` hoặc [`wrk`](https://github.com/wg/wrk): đánh giá tốc độ web servers

- `strace`: debug lời gọi hệ thống 

- [`mtr`](http://www.bitwizard.nl/mtr/): công cụ tốt hơn traceroute khi debug mạng 

- `cssh`: mô phỏng shell đồng thời 

- `rsync`: đồng bộ các file thông qua SSH hoặc local 

- [`wireshark`](https://wireshark.org/) và [`tshark`](https://www.wireshark.org/docs/wsug_html_chunked/AppToolstshark.html): theo dõi gói tin và debug mạng

- [`ngrep`](http://ngrep.sourceforge.net/): grep với dữ liệu ở tầng mạng 

- `host` và `dig`: tìm kiếm trong DNS

- `lsof`: thông tin miêu tả file (file descriptor) và socket (thực ra cũng là một loại file) của tiến trình

- `dstat`: thông kê hệ thống hữu ích 

- [`glances`](https://github.com/nicolargo/glances): cái nhìn tổng quan trên nhiều hệ thống con

- `iostat`: Thông kê tình trạng sử dụng đĩa cứng 

- `mpstat`: Thống kê tình trạng sử dụng CPU 

- `vmstat`: Thống kê tình trạng sử dụng bộ nhớ 

- `htop`: Phiên bản cải tiến của lệnh `top` 

- `last`: Lịch sử login 

- `w`: Ai đang login trong hệ thống 

- `id`: thông tin về định danh về user/group

- [`sar`](http://sebastien.godard.pagesperso-orange.fr/): Thống kê hệ thống theo thời gian 

- [`iftop`](http://www.ex-parrot.com/~pdw/iftop/) hoặc [`nethogs`](https://github.com/raboof/nethogs): tiện ích theo dõ mạng bằng socket hoặc tiến trình process

- `ss`: Thống kê socket 

- `dmesg`: hiển thị log lúc boot và log hệ thống 

- `sysctl`: xem và cấu hình nhân tham số nhân Linux lúc đang chạy (có gì đó không đúng lắm)

- `hdparm`: Các thao tác/đánh giá hiệu năng với ổn đĩa giao tiếp bằng SATA/ATA

- `lsblk`: Danh sách các thiết bị block : một biểu diễn dạng cây của đĩa cứng và các phân vùng của nó 

- `lshw`, `lscpu`, `lspci`, `lsusb`, `dmidecode`: thông tin phần cứng, bao gồm CPU, BIOS, RAID, graphics, devices, etc.

- `lsmod` and `modinfo`: danh sách và chi tiết các module của nhân

- `fortune`, `ddate`, và `sl`: ùi, cái này phụ thuộc vào việc bạn coi cái đầu máy hơi nước và các câu quote chớp nhoáng có "hữu ích hay không".


## Chỉ chạy trên OS X 

These are items relevant *only* on OS X.

- Trình quản lý gói phần mềm `brew` (Homebrew) và/hoặc `port` (MacPorts). Những cái này sử dụng để cài rất nhiều công cụ được nói đến ở trên trên OS X.

- Sao chép bất cứ đầu ra của câu lệnh nào lên một ứng dụng desktop sử dụng `pbcopy`, rồi đưa nó trở thành đầu vào của một câu lệnh sử dụng `pbpaste`.

- Để cho phép sử dụng phím Option trong terminal của OS X như là phím alt key ( được sử dụng trong rất nhiều tình huống như **alt-b**, **alt-f**, etc.), Mở Preferences -> Profiles -> Keyboard và chọn "Use Option as Meta key".

- Để mở một file bằng một desktop từ dòng lệnh, sử dụng  `open` hoặc `open -a /Applications/Whatever.app`.

- Spotlight: Tìm kiếm file bằng lệnh `mdfind` và liệt kê danh sách các metadata (như thông tin EXIF của ảnh) bằng lệnh `mdls`.

- Hiểu rằng OS X dựa trên BSD Unix, và có rất nhiều câu lệnh (ví dụ `ps`, `ls`, `tail`, `awk`, `sed`) có các dị bản so với Linux, cái hầu hết bị ảnh hưởng của System V-style Unix và GNU tools. Bạn có thể nói đến sự khác biệt trong các trang manunal (man page) có phần mở đầu là "BSD General Commands Manual". Ở một số trường hợp, phiên bản GNU cũng được cài đặt (như `gawk` và `gsed` tức là GNU awk và sed). Nếu bạn định viết một script Bash chạy cross-platform, nên tránh sử dụng những câu lệnh kiểu đó ( ví dụ, có thể xem xét sử dụng Python hoặc `perl`) hoặc là phải test kĩ vào.

- Để lấy thông tin về phiên bản OS X, sử dụng `sw_vers`.

## Chỉ chạy trên Windows 

 Những cái dưới đây *chỉ* chạy trên Windows thôi đấy.

### Cách để có được cái tool Unix trên môi trường Windows 

- Để sử dụng sức mạnh của Unix shell trong môi trường Microsoft Windows, hãy cài đặt [Cygwin](https://cygwin.com/). Hầu hết câu lệnh trong tài liệu này có thể làm việc thoải mái.

- Trên Windows 10, bạn có thể cài [Bash on Ubuntu on Windows](https://msdn.microsoft.com/commandline/wsl/about), cái cung cấp môi trường Bash với các câu lệnh Unix trên đó. Thêm nữa, cái này cho phép chạy một chương trình Linux trên Windows. Tuy nhiên, nó lại không hỗ trợ việc chạy một ứng dụng Windows từ dòng lệnh của Bash.

- Nếu bạn muốn sử dụng các công cho dành developer của GNU (như GCC) trên Windows, hãy xem thử [MinGW](http://www.mingw.org/) xem và gói [MSYS](http://www.mingw.org/wiki/msys) của nó nữa, nó sẽ cung cấp các công cụ như bash, gawk, make và grep. MSYS không có được các tính năng nhiều như Cygwin. MinGW là dành việc cho việc tạo tạo một môi trường hỗ trợ native Windows của các Unix tools.

- Một cách khác để có các công cụ Unix trên Windows l [Cash](https://github.com/dthree/cash). Chú ý là chỉ một vài câu lệnh, một vài option được hỗ trợ trên môi trường này.

### Công cụ dòng lệnh hữu dụng trên Windows 

- Bạn có thể thực hiện và viết script cho hầu hết các tác vụ quản trị hệ thống trên Windows từ dòng lệng bằng cách học và sử dụng câu lệnh `wmic`.

- Câu công cụ dòng lệnh có sẵn trên Windows liên quan đến mạng bao gồm `ping`, `ipconfig`, `tracert`, và `netstat`.

- Bạn có thể thực hiện rất nhiều [many useful Windows tasks](http://www.thewindowsclub.com/rundll32-shortcut-commands-windows) bằng cách gọi lệnh `Rundll32`.

### Các mẹo dùng trên Cygwin 

- Cài đặt thêm các chương trình Unix bằng trình quản lý gói của Cygwin - Cygwin's package manager.

- Sử dụng `mintty` là cửa sổ dòng lệnh.

- Truy cập Windows clipboard thông qua file `/dev/clipboard`.

- Chạy `cygstart` để mở một file thông qua chương trình đã được đăng kí để chạy nó

- Truy cập registry trong Windows sử dụng `regtool`.

- Chú ý rằng đường dẫn thư mục gốc ổ đĩa `C:\` sẽ trở thành `/cygdrive/c` khi chạy ở  Cygwin, và thư mục root của Cygwin `/` thường sẽ nằm ở `C:\cygwin` trên Windows Windows. Chuyển đổi giữa đường dẫn giữa Cygwin và Windows-style bằng lệnh `cygpath`. Đây là hầu hết các công cụ hữu ích khi chạy một chương trình windows.

## Xem thêm 

- [awesome-shell](https://github.com/alebcay/awesome-shell): A curated list of shell tools and resources.
- [awesome-osx-command-line](https://github.com/herrbischoff/awesome-osx-command-line): A more in-depth guide for the OS X command line.
- [Strict mode](http://redsymbol.net/articles/unofficial-bash-strict-mode/) for writing better shell scripts.
- [shellcheck](https://github.com/koalaman/shellcheck): A shell script static analysis tool. Essentially, lint for bash/sh/zsh.
- [Filenames and Pathnames in Shell](http://www.dwheeler.com/essays/filenames-in-shell.html): The sadly complex minutiae on how to handle filenames correctly in shell scripts.
- [Data Science at the Command Line](http://datascienceatthecommandline.com/#tools): More commands and tools helpful for doing data science, from the book of the same name

## Disclaimer

With the exception of very small tasks, code is written so others can read it. With power comes responsibility. The fact you *can* do something in Bash doesn't necessarily mean you should! ;)


## License

[![Creative Commons License](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-sa/4.0/)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).
