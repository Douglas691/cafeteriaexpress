# cafeteria
cafeteria/
│
├── app.py
├── static/
│   └── style.css
├── templates/
│   ├── index.html
│   └── menu.html
from flask import Flask, render_template

app = Flask(__name__)

# Página inicial
@app.route('/')
def home():
    return render_template('index.html')

# Página do cardápio
@app.route('/menu')
def menu():
    itens = [
        {"nome": "Café Expresso", "preco": "R$ 5,00"},
        {"nome": "Cappuccino", "preco": "R$ 7,00"},
        {"nome": "Latte", "preco": "R$ 6,50"},
        {"nome": "Bolo de Cenoura", "preco": "R$ 8,00"},
    ]
    return render_template('menu.html', itens=itens)

if __name__ == '__main__':
    app.run(debug=True)
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Bem-vindo à Cafeteria</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>
    <h1>☕ Bem-vindo à nossa Cafeteria!</h1>
    <p>Aqui servimos o melhor café da cidade.</p>
    <a href="/menu">Ver Cardápio</a>
</body>
</html>
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Cardápio</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>
    <h1>🍽️ Cardápio</h1>
    <ul>
        {% for item in itens %}
            <li>{{ item.nome }} - <strong>{{ item.preco }}</strong></li>
        {% endfor %}
    </ul>
    <a href="/">Voltar</a>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #f3f3f3;
    padding: 20px;
    text-align: center;
}

h1 {
    color: #6b3e26;
}

a {
    display: inline-block;
    margin-top: 20px;
    color: #fff;
    background-color: #6b3e26;
    padding: 10px 20px;
    text-decoration: none;
    border-radius: 5px;
}

a:hover {
    background-color: #8b5e3c;
}
python app.py
