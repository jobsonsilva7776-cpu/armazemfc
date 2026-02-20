<script>
const form = document.getElementById("formPeneira");
const tabela = document.querySelector("#tabela tbody");

function carregar(escudo-armazem.png){
    const inscritos = JSON.parse(localStorage.getItem("inscricoes")) || [];
    tabela.innerHTML = "";

    inscritos.forEach((p, index) => {
        tabela.innerHTML += `
        <tr>
            <td>${p.nome}</td>
            <td>${p.idade}</td>
            <td>${p.categoria}</td>
            <td><th>Ação</th>
                <button onclick="excluir(${index})" style="background:red;color:white;border:none;padding:5px;border-radius:5px;cursor:pointer;">
                    Excluir
                </button>
            </td>
        </tr>`;
    });
}

form.addEventListener("submit", function(e){
    e.preventDefault();

    const inscricao = {
        nome: nome.value,
        idade: idade.value,
        data: data.value,
        telefone: telefone.value,
        categoria: categoria.value
    };  

    const inscritos = JSON.parse(localStorage.getItem("inscricoes")) || [];
    inscritos.push(inscricao);
    localStorage.setItem("inscricoes", JSON.stringify(inscritos));

    form.reset();
    carregar();
});

function excluir(index){
    const inscritos = JSON.parse(localStorage.getItem("inscricoes")) || [];
    inscritos.splice(index, 1);
    localStorage.setItem("inscricoes", JSON.stringify(inscritos));
    carregar();
}

carregar();
</script>
