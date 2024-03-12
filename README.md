<?php
session_start();

// Verifica se a variável de sessão existe
if (!isset($_SESSION['contador'])) {
    // Inicia o contador se não existir
    $_SESSION['contador'] = 1;
} else {
    // Incrementa o contador se já existir
    $_SESSION['contador']++;

    // Zera o contador se for a quarta pessoa
    if ($_SESSION['contador'] > 3) {
        $_SESSION['contador'] = 1;
    }
}

// Define os links do WhatsApp com base no contador
$links = [
    1 => 'https://link-whatsapp-1.com',
    2 => 'https://link-whatsapp-2.com',
    3 => 'https://link-whatsapp-3.com'
];

// Redireciona para o link correspondente
header("Location: " . $links[$_SESSION['contador']]);
exit();
?>
