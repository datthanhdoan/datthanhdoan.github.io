---
title: "Aseprite - Pixel Art Tool" 
date: 2023-12-13
description: "Aseprite is a pixel art tool that lets you create 2D animations for videogames."
tags: ["game", "tools"]
showLikes: true
showComments: true
cascade:
  showReadingTime: true
---
## Giới thiệu
Nếu bạn yêu thích làm game , đặc biệt là game pixel thì chắc hẳn bạn đã không xa lạ gì với Aseprite . Nó là một công cụ mạnh mẽ cho vẽ pixel art và animation 2D và bản 1.3.x mới ra còn giúp bạn chỉnh sửa tilemap nữa .
Với mình , một sinh viên đang học làm game và muốn tìm hiểu thêm về pixel art thì đây là một công cụ tuyệt vời rồi . Nhưng Aseprite không hề miễn phí và bạn phải trả 19.99$ (~ 485.377vnd) 🫠 . 
### Trả phí ?
Nghe đến đây thì bạn lại tưởng tôi co rack nó đúng ko ? 😤
Hmmm , **không đâu** . Bởi vì có thể bạn không biết , aseprite là một phần mềm mã nguồn mở và bạn hoàn toàn có thể tự build nó từ source code chính thức của [aseprite](https://github.com/aseprite/aseprite) trên github. Nghe đến đây thì bạn kiểu "Mọe ông phét à , thu tiền thì nó để nguồn mở để làm gì ?" . Thật ra thì bạn có thể tự build nó từ source code nhưng bạn không được phép bán nó hay phân phối nó . Bạn chỉ được dùng nó cho mục đích cá nhân thôi . Nếu bạn muốn dùng nó cho mục đích thương mại thì bạn phải mua bản quyền . Và cũng không phải ai cũng có thể tự build nó được đâu 😉. 
## Vậy làm sao để build nó ?
Nếu bạn là học cntt hoặc liên quan đến lập trình thì hẳn không quá khó khăn . Đây là link hướng dẫn chính thức của [Aseprite](https://github.com/aseprite/aseprite/blob/main/INSTALL.md) . Ở bài viết này mình sẽ hướng dẫn các bạn build nó trên Window.
### Dependencies
Bạn cần phải có những thứ sau để có thể build được Aseprite :
- [Cmake](https://cmake.org/download/) và [Ninja](https://ninja-build.org/) ,[Skia](https://github.com/aseprite/skia) của Asprite .
- Visual Studio 2022 ( ở đây mình dùng bản 2022 ). Bạn cần chọn [Desktop development with C++ item](https://imgur.com/a/7zs51IT) Và win 10 SDK (trong phần Individual components) *Nếu dùng win11 thì bạn hãy chọn win 11 SDK nhé*
### Build
- Step 1: Clone repo của Aseprite về máy của bạn .
Clone repo của Aseprite về máy của bạn .
*Lưu ý : Bạn phải clone nó ở thư mục C:\ , không phải thư mục tên của bạn đâu nhé!* 
    ```bash
    git clone --recursive https://github.com/aseprite/aseprite.git

    # Sau đó cập nhật submodules
    cd aseprite
    git pull
    git submodule update --init --recursive
    ```

- Step 2: Download Skia và cài đặt Cmake và Ninja
    - Tạo thư mục "C:\deps\skia"
    - Bạn tải file Zip trong realease của Skia về và giải nén nó . Sau đó bạn copy nội dung bên trong vào thư mục C:\deps\skia
    - Tiếp đến là bạn hãy cài Cmake và Ninja. Mình khuyên các bạn nên dùng [scoop](https://scoop.sh/) để cài đặt cho nhanh và dễ dàng hơn . 

- Step 3: Build Aseprite
Mở Cmd lên và gõ lệnh sau :
    ```cmd
    call "C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\Tools\VsDevCmd.bat" -arch=x64
    ```
    Sau đó bạn gõ lệnh sau để build :
    ```
    cd aseprite
    mkdir build
    cd build
    cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo -DLAF_BACKEND=skia -DSKIA_DIR=C:\deps\skia -DSKIA_LIBRARY_DIR=C:\deps\skia\out\Release-x64 -DSKIA_LIBRARY=C:\deps\skia\out\Release-x64\skia.lib -G Ninja ..
    ninja aseprite
    ```
    Well cái này sẽ mất thời gian phụ thuộc vào cấu hình máy của bạn . 
- Step 4: Tạo shortcut cho Aseprite trong Start Menu.

    - Tạo một thư mục tên là "**Aseprite**" trong "C:\Program Files (x86)\" . Sau đó copy **aseprite.exe** và folder **data** ( đây là hai thứ bạn vừa build xong nó nằm ở "C:\aseprite\build\bin" ) vào "Aseprite". 
    - Ấn chuột phải vào **aseprite.exe** và chọn "**Create shortcut**" . Sau đó bạn copy và paste shortcut đó vào "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\" (*Nếu shortcut tên là "aseprite.exe - Shortcut" hoặc đại loại vậy thì bạn hãy đổi tên nó thành "Aseprite" nhé*).

And that it 🥳 ! Bây giờ bạn có thể mở Aseprite lên và sử dụng nó rồi .
