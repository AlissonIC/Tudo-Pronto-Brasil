Descrição: script de busca de endereço por cep para WooCommerce (Wordpress) ou demais ferramentas.

Wordpress:
```html

<script>
	// Script para consulta de CEP (Busca campos pelos ID default da tela de checkout do Woocomerce)
	jQuery("#billing_postcode").on('change', function ($e){
		var cep = $(this).val();
		cep = cep.replace("-","");
		if(cep.length == 8){
			jQuery.ajax({
				type: 'GET',
				url: 'https://viacep.com.br/ws/'+cep+'/json/',
				success:function(json){ 
					jQuery("#billing_address_1").val(json.logradouro);
					jQuery("#billing_neighborhood").val(json.bairro);
					jQuery("#billing_city").val(json.localidade);
					jQuery("#estado option[value='"+json.uf+"']").attr('selected','selected');
					jQuery('#select2-billing_state-container').selectpicker('refresh');
				}
			})
		}
	});
</script>

```

Ferramentas que não são Wordpress:
```html

<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.5.1/jquery.min.js" integrity="sha512-bLT0Qm9VnAYZDflyKcBaQ2gg0hSYNQrJ8RilYldYQ1FxQYoCLtUjuuRuZo+fjqhx/qtq/1itJ0C2ejDxltZVFg==" crossorigin="anonymous"></script>
<script>
	// Script para consulta de CEP (Busca campos pelos ID default)
	$("#billing_postcode").on('change', function ($e){
		var cep = $(this).val();
		cep = cep.replace("-","");
		if(cep.length == 8){
			jQuery.ajax({
				type: 'GET',
				url: 'https://viacep.com.br/ws/'+cep+'/json/',
				success:function(json){ 
					$("#billing_address_1").val(json.logradouro);
					$("#billing_neighborhood").val(json.bairro);
					$("#billing_city").val(json.localidade);
					$("#estado option[value='"+json.uf+"']").attr('selected','selected');
					$('#select2-billing_state-container').selectpicker('refresh');
				}
			})
		}
	});
</script>

```
