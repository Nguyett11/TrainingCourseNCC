# Phần 1: Definition
## 1. Git là gì? 
  - Hệ thống quản lý phiên bản phân tán (Distributed Version Control System).
  - Dùng để quản lý mã nguồn, theo dõi thay đổi và làm việc nhóm.
## 2. Git và GitHub
  - Git là công cụ quản lý mã nguồn.
  - GitHub là dịch vụ lưu trữ Git repository online. (Ngoài ra còn có GitLab, Bitbucket…)
  
# Phần 2: Cài đặt và Cấu hình
## 1. Cài git: Tải tại git-scm.com
## 2. Cấu hình: 
      git config --global user.name "Tên"
      git config --global user.email email@example.com
## 3. Kiểm tra cấu hình: git config –list

# Phần 3: Làm việc với Repository
  - Tạo repo mới: git init
  - Clone repo có sẵn: git clone <url>
  - Kiểm tra trạng thái: git status
  - Thêm thay đổi vào stagging: git add <file> hoặc git add .
  - Commit git commit -m “…”
  - Xem lịch sử commit: git log hoặc git log –oneline
    
# Phần 4: Nhánh (Branch)
  - Tạo nhánh: git branch <Tên nhánh>
  - Chuyển nhánh: git checkout <Tên nhánh>
  - Tạo và chuyển nhanh: git checkout -b <Tên nhánh>
  - Xem danh sách nhánh: git branch
  - Xóa nhánh: git branch -d <Tên nhánh>
    
# Phần 5: Gộp nhánh và xử lý conflict
  - Gộp nhánh: Git merge <nhánh>
  - Xử lý conflict:
    •	Sửa file bị xung đột
    •	Git add <file>
    •	Git commit
  - Rebase: git rebase <nhánh> (nối commit theo dòng thẳng)
    
# Phần 6: Git remote (làm việc với server)
  - Kiểm tra remote: git remote -v
  - Thêm remote: git remote add origin <url>
  - Push lên github: git push -u origin main
  - Pull về máy: git pull origin main
  - Đổi nhánh chính (nếu dùng master): git branch -M main
    
# Phần 7: Các lệnh nâng cao
  - Undo file đã thay đổi: git checkout -- <file>
  - Hủy toàn bộ thay đổi chưa commit: git reset –hard 
  - Hủy 1 commit: git revert <commit-id>
  - Chạy lại commit (soft reset): git reset --soft <commit-id>
  - Xem khác biệt: git diff, git diff –staged
  - Stash (giấu tạm thời thay đổi): git stash, git stash apply
    
# Phần 8: Commit Convention
- Quy tắc giúp commit dễ hiểu, rõ ràng, thống nhất khi làm việc nhóm. Ví dụ theo chuẩn Conventional Commits:
 
   `<type>(scope): message`
  - type: loại commit (feat, fix, refactor, docs, test, chore, ...)
  - scope: phạm vi thay đổi (không bắt buộc)
  - message: mô tả ngắn gọn, rõ ràng

- Các loại convention commit:
		> Feat: thêm 1 feature.
		> Fix: fix bug của hệ thống, vá lỗi.
		> Refactor: sửa code nhưng không fix bug cũng không thêm feature hoặc đôi lúc fix bug từ việc này.
		> Docs: thêm/thay đổi document.
		> Chore: những sửa đổi nhỏ nhặt không liên quan tới code.
		> Style: những thay đổi không làm thay đổi ý nghĩa của code như css, ui.
		> Perf: code cải tiến hiệu suất xử lý.
		> Vendor: cập nhật version cho các module, packages, dependencies,..
  
Ví dụ:
  feat(user): add user login form
  fix(api): correct null pointer error
  docs(readme): update project description

# Phần 9: Practices
- Luôn tạo branch mới khi làm tính năng/bugfix (feature/login, bugfix/api-crash)
- Viết commit message rõ ràng, có ý nghĩa
- Pull trước khi push để tránh xung đột
- Không commit file rác hoặc file cấu hình cục bộ (dùng .gitignore)
- Squash commit khi merge vào main để gọn lịch sử

# Phần 10: Rewrite history with git rebase
## 1. Git rebase là gì?
git rebase là lệnh giúp thay đổi lại lịch sử commit của một nhánh bằng cách:
- Di chuyển các commit của bạn lên đầu của nhánh khác.
- Làm sạch lại lịch sử commit cho gọn gàng, tuyến tính (linear).
- Tránh tạo merge commit không cần thiết như khi dùng git merge.
## 2. Khi nào dùng git rebase?
- Khi bạn muốn cập nhật nhánh đang làm việc từ nhánh chính (main, master) nhưng vẫn giữ lịch sử commit gọn gàng.
- Khi muốn chỉnh sửa lại nội dung commit (sử dụng git rebase -i).
- Khi muốn gộp nhiều commit thành một (squash).

# Phần 11: Undo-like faulty commit with git revert
## 1. Git revert là gì?
- git revert là lệnh dùng để đảo ngược một commit bị lỗi, nhưng không thay đổi lịch sử commit hiện có.
- Khi bạn revert một commit, Git tạo ra một commit mới có nội dung ngược lại để "hủy bỏ" các thay đổi của commit lỗi kia.
## 2. Khi nào dùng git revert?
- Khi bạn đã push commit lỗi lên nhánh chung như main hoặc develop.
- Khi bạn cần giữ nguyên lịch sử commit để người khác còn tham chiếu tới nó (đối tác, CI/CD, ticket…).
- Đảm bảo các pull request hoặc release nào cần lịch sử không bị rewrite.

# Phần 12: Replace code in master branch to temp branch
## 1. “Replace code in master branch to temp branch” nghĩa là: 
Bạn muốn lấy toàn bộ mã nguồn hiện tại của nhánh master và thay thế (ghi đè) toàn bộ mã trong nhánh temp bằng nó.
## 2. Khi nào dùng?
- Khi bạn có một nhánh tạm (temp, backup, test) đã cũ hoặc bị lỗi.
- Và bạn muốn cập nhật nó theo đúng phiên bản mới nhất từ master.
- Có thể dùng để reset nhánh temp về lại trạng thái "sạch" như master.
