#development #python #django 

class Casing(models.Model):  
    objects = models.Manager()  
    casing = models.PositiveSmallIntegerField(choices=CasingChoice.choices)  
    material = models.PositiveSmallIntegerField(choices=MaterialChoice.choices)  
    price = models.DecimalField(max_digits=10, decimal_places=2)  
  
    class Meta:  
        constraints = [  
            models.UniqueConstraint(fields=['casing', 'material'], name='unique_casing_material')  
        ]  
    def __str__(self):  
        return f'{self.get_casing_display()} - {self.get_material_display()} - {self.price} руб.'

class CasingChoice(IntegerChoices):  
    FIGURE_76 = (1, 'Фигурный 76')  
    FIGURE_98 = (2, 'Фигурный 98')  
    CORNICE_120 = (3, ' Карниз 120')  
    PREMIER_1 = (4, 'Премьер 1')  
    PREMIER_2 = (5, 'Премьер 2')  
    PREMIER_1_WITH_CORNICE = (6, 'Премьер 1 c карнизом')  
    PLAIN_90_DEGREE = (7, 'Прямой 90 градусов')
        
[[Метод для автосоздания  slug' ов в Django]]
[[Создание абстрактного класса базовой модели в Django]]
[[Создание функции для сохранения медиа файлов в Django]]
[[Установка ViewsSet в Django ulr]]