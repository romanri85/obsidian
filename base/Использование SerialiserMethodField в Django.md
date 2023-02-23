#development #python #django 

class ProductVariant(BasicModel):  
    name = models.CharField(max_length=255)  
    product = models.ForeignKey(Product, on_delete=models.CASCADE, related_name='product_variants')  
    image = models.ImageField(upload_to=upload_variant_image_path, blank=False,  
                              validators=[validate_image_file_extension])  
    price = models.DecimalField(max_digits=7, decimal_places=0)  
    material = models.PositiveSmallIntegerField(choices=MaterialChoice.choices)  
    glass = models.ForeignKey(Glass, on_delete=models.CASCADE, related_name='product_variants', null=True, blank=True)  
  
    def __str__(self):  
        return f'{self.name}'  
  
    class Meta:  
        verbose_name = _('Product variant')  
        verbose_name_plural = _('Product variants')

class ProductVariantSerializer(serializers.ModelSerializer):  
    material_color = serializers.SerializerMethodField(method_name='get_material_color')  
  
    def get_material_color(self, obj: ProductVariant):  
        choice = material_color_map[obj.material].choices  
        return dict(choice)  
  
    class Meta:  
        model = ProductVariant  
        fields = ['id', 'name', 'product', 'material_color', 'image', 'price', 'material', 'glass']

class EnamelColorChoice(IntegerChoices):  
    RAL_9003 = (51, 'RAL 9003 ')  
    RAL_1013 = (52, 'RAL 1013 ')  
    RAL_1019 = (53, 'RAL 1019 ')  
    RAL_7030 = (54, 'RAL 7030 ')  
    RAL_7037 = (55, 'RAL 7037 ')  
    RAL_9010 = (56, 'RAL 9010 ')  
  
  
material_color_map = {  
    MaterialChoice.OAK: OakColorChoice,  
    MaterialChoice.BEECH: BeechColorChoice,  
    MaterialChoice.ENAMEL: EnamelColorChoice,  
}