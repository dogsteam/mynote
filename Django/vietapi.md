tạo server api

1. cài thư viện django restframework 
```
pip install djangorestframework
```
link video:  https://youtu.be/gmaT-8WoirE

#2 Định nghĩa chuỗi json cần gửi lên server thông qua serializer 

1. tqaoj file serializer.py

```python
from rest_framework import serializers

class KeySerializer(serializers.Serializer):
    tinnhan = serializers.CharField(max_length=50, required=True)
```

2. Tao API View ơ trong file view để sửl ý khi mà máy khác gọi api 

```python

from rest_framework.views import APIView
from rest_framework.response import Response
from rest_framework import status
from .serializer import KeySerializer



class GetAllCouse(APIView):
    def post(self, request):
        validate = KeySerializer(data=request.data)

        if not validate.is_valid():
            return Response('may gui sai du lieu roi', status=status.HTTP_400_BAD_REQUEST)

        mykey = validate.data['tinnhan']
        print("tin nhan=")
        print(mykey)


        return Response('thanh cong', status=status.HTTP_200_OK)

```


# them url
```
from django.urls import path
from backend.views import IndexView, GetAllCouse

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', IndexView.as_view()),
    path('api-test/', GetAllCouse.as_view()),
]

```

