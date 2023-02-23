#development #python #django 

class BasicModel(models.Model):  
    objects = models.Manager()  
    created_at = models.DateTimeField(auto_now_add=True)  
    updated_at = models.DateTimeField(auto_now=True)  
  
    class Meta:  
        abstract = True
[[Метод для автосоздания  slug' ов в Django]]
[[Создание функции для сохранения медиа файлов в Django]]
[[Установка ViewsSet в Django ulr]]
[[Создание абстрактного класса базовой модели в Django]]
