#development #python #django 

def upload_material_color_image(instance, filename):  
    return f'material_color_images/{instance.product_variant_id}/{filename}'  
  
  
class MaterialColorProductVariant(models.Model):  
    color = models.PositiveSmallIntegerField()  
    price = models.DecimalField(max_digits=10, decimal_places=2)  
    # material = models.PositiveSmallIntegerField(choices=MaterialChoice.choices)  
    product_variant = models.ForeignKey('ProductVariant', on_delete=models.CASCADE, related_name='material_colors')  
    image = models.ImageField(upload_to=upload_material_color_image, blank=False,  
                              validators=[validate_image_file_extension])
                              
[[Метод для автосоздания  slug' ов в Django]]
[[Установка ViewsSet в Django ulr]]
[[Создание абстрактного класса базовой модели в Django]]
[[Создание таблицы с полем choices в Django]]