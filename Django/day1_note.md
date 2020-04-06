# NEW PROJECT
## Import Django
```
py -m pip install Django
```
## Tao project django bằng câu lệnh. Thêm dấu . để tạo trong thư mục hiện tại, còn bỏ dấu chấm ra thì tạo thêm thư mục nữa 
```
django-admin startproject tenproject .
```
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
                        path('', IndexView.as_view()),                 #đường dẫn gọi đến hamtest   
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
        
        ##
        
        Để gửi get request lấy dữ liệu từ 1 server bất kỳ 
        
        cần :
        ## link của api 
        ## các tham số cần thiết
        
        Thư viện cần thư viện 
        ```
        requests
        ```
        
        cách cài ``` pip install requests``
        
        ```python
        
        import requests
import json


r = requests.get("https://graph.facebook.com/3132894833388356?fields=name&access_token=EAAdZAypcTckcBANZBy1F8ZCF3NA7SSRJQIkqLitTJQ2SXRH1uj6maJGVZAPnUw7BlQTWndHWZA8qKNjDS5qil0y0BztSFcUmvmBCTjswpV4qBPDhZAK9u1sWrLID2RtUvKVPPCzFZCZACIFPbrWpqjUY4r7NKao75Fon0SRReREzZCWEbzZAuJPYqqZAhR7thiAw5EnRVSJSEHyQjWg53l3infr")
print(r.content)
a = json.loads(r.text)
print('title la:', a['name'])
        
        ```
       
