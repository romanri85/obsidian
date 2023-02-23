#development #python #django #drf 

from django.urls import path, include  
from rest_framework import routers  
from . import views  
  
  
router = routers.DefaultRouter()  
router.register('colors', views.ColorViewSet)  
router.register('hardware', views.HardwareViewSet)  
  
urlpatterns = [  
    path('', include(router.urls))
            
]

[[Метод для автосоздания  slug' ов в Django]]
[[Создание функции для сохранения медиа файлов в Django]]
[[Создание абстрактного класса базовой модели в Django]]