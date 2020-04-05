Tao project django bằng câu lệnh

```
django-admin startproject tenproject .
```
Thêm dấu . để tạo trong thư mục hiện tại, còn bỏ dấu chấm ra thì tạo thêm thư mục nữa 

## Tạo project 
django-admin startproject tenproject .
## Chạy test
``` 
python manage.py runserver
```
## Tạo app trong project
```
python manager.py startapp appname
```
## Chạy demo web
```
1. Tạo thư mục templates trong thư mục project, thư mục này chứa các file hiển thị
2. Chỉnh trong settings đường dẫn 'DIRS': [os.path.join(BASE_DIR, 'templates')], đến thư mục templates vừa tạo
3. Viết hàm định tuyến URL đến thư mục template trong urls.py 
                    from backend.views import hamtest #import hàm từ trong views.py, nằm trong project backend
                    urlpatterns = [
                        path('admin/', admin.site.urls),   #demo
                        path('', hamtest),                 #đường dẫn gọi đến hamtest   
                    ]
4. Trong views.py
                    def hamtest(request):                    #định nghĩa hàm với biến request 
                        return render(request, "index.html") #trả về render file html
```
## Test truyền biến qua form

    def post(self, request):
        so1 = request.POST.get('soa')    #Nhận biến từ POST
        so2 = request.POST.get('sob')
        tong =  int(so1) + int(so2)      #Toán tử 
        hieu = int(so1) - int(so2)
        context = {                      #Kiểu dữ liệu   dict         
            'tong': tong,
            'hieu': hieu

        }
        return render(request, "index.html", context)   #Trả về file html với context
        
