#development #python #django #drf

def save(self, *args, **kwargs):  
    if not self.slug:  
        self.slug = slugify(f'hardware-{self.name}')  
    super(Hardware, self).save(*args, **kwargs)

[[Установка ViewsSet в Django ulr]]
[[Создание функции для сохранения медиа файлов в Django]]
[[Создание таблицы с полем choices в Django]]
[[Установка ViewsSet в Django ulr]]
[[Создание абстрактного класса базовой модели в Django]]
