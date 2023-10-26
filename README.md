# t
# paginação
{% extends 'base.html' %}

{% block center %}
<div class="row">
    <div class="col-md-4">
      <form method="GET">
        {{ filter.form.as_p }}
        <input type="submit" />
      </form>
    </div>

    <div class="col-md-8">
      <table class="table">
        <thead>
          <tr>
            <th></th>
          </tr>
        </thead>
        <tbody>
          {% for obj in page_obj %}
            <tr>
              <td>{{ obj.}}</td>
            </tr>
          {% endfor %}
        </tbody>
      </table>
    </div>
  </div>
<div class="container pt-3">
  <nav aria-label="Page navigation example">
    <ul class="pagination">
      {% if page_obj.has_previous %}
        <li class="page-item"><a class="page-link" href="?page={{ page_obj.previous_page_number }}">Anterior</a></li>
      {% endif %}

      {% for page in page_obj.paginator.page_range %}
        <li class="page-item"><a class="page-link" href="?page={{ page }}">{{ page }}</a></li>
      {% endfor %}

      {% if page_obj.has_next %}
        <li class="page-item"><a class="page-link" href="?page={{ page_obj.next_page_number }}">Próxima</a></li>
      {% endif %}
    </ul>
  </nav>
</div>

  {% endblock %}

 page_number = request.GET.get("page")
 page_obj = paginator.get_page(page_number)
    
# formulário
{% extends 'base.html' %}

{% block center %}
    <h2> Formulário de Matricula.</h2>
       
    <form method="post">
        {% csrf_token %}
        <div class="mb-3">
            <label for="nome" class="form-label"></label>
            {{ form. }}
        </div>
        <button type="submit" class="btn btn-primary">Enviar</button>
    </form>    
{% endblock %}

# listar

    <a href="{% url 'aluno_criar' %}" class="btn btn-success mb-3">Novo Cadastro</a>

    <table class="table table-bordered">

    tabela aqui

      <td>
                    <a href="{% url '_editar' id=obj.id %}" class="btn btn-primary btn-sm">Editar</a>
                    <a href="{% url '_remover' id=obj.id %}" class="btn btn-danger btn-sm">Remover</a>
      </td>
   
# form
from django.forms import ModelForm
from django import forms
from .models import 

class ReservaForm(ModelForm):

    class Meta:
        model = 
        fields = '__all__'
        widgets = {
            '' : forms.TextInput(attrs={'class': 'form-control' }),

  # views filter
  def _filtrar(request):
  template_name = '/filter.html'
  object_list = Reserva.objects.all()
  _filter = Filter(request.GET, queryset=object_list)

    context = {
        'object_list': object_list,
        'filter': _filter
    }
    return render(request, template_name, context)

  
