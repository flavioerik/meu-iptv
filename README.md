<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Venda IPTV - Teste 6 Horas</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap');
    
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins', sans-serif;
    }
    
    body {
      background: linear-gradient(135deg, #1e3c72, #2a5298);
      color: #fff;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 30px 15px;
      overflow-x: hidden;
    }
    
    header {
      margin-bottom: 40px;
      text-align: center;
      animation: fadeInDown 1s ease forwards;
    }
    
    header h1 {
      font-size: 2.8rem;
      margin-bottom: 10px;
      letter-spacing: 2px;
      text-shadow: 2px 2px 8px #000;
    }
    
    header p {
      font-size: 1.1rem;
      color: #b0d9ff;
    }
    
    @keyframes fadeInDown {
      0% { opacity: 0; transform: translateY(-30px); }
      100% { opacity: 1; transform: translateY(0); }
    }
    
    main {
      background: rgba(255, 255, 255, 0.1);
      border-radius: 12px;
      padding: 30px 40px;
      width: 100%;
      max-width: 400px;
      box-shadow: 0 8px 30px rgba(0,0,0,0.4);
      animation: fadeInUp 1s ease forwards;
    }
    
    @keyframes fadeInUp {
      0% { opacity: 0; transform: translateY(30px); }
      100% { opacity: 1; transform: translateY(0); }
    }
    
    .plan {
      background: #007aff;
      border-radius: 10px;
      padding: 20px;
      text-align: center;
      box-shadow: 0 6px 20px rgba(0, 122, 255, 0.7);
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      cursor: pointer;
    }
    
    .plan:hover {
      transform: scale(1.05);
      box-shadow: 0 10px 30px rgba(0, 122, 255, 1);
    }
    
    .plan h2 {
      font-size: 1.8rem;
      margin-bottom: 10px;
      letter-spacing: 1.2px;
    }
    
    .plan p {
      font-size: 1.1rem;
      margin-bottom: 20px;
    }
    
    .price {
      font-size: 2rem;
      font-weight: 700;
      margin-bottom: 20px;
      color: #ffdd57;
      text-shadow: 1px 1px 5px #b38600;
    }
    
    .btn-whatsapp {
      display: inline-flex;
      align-items: center;
      background: #25D366;
      color: #fff;
      padding: 12px 25px;
      font-size: 1.1rem;
      border-radius: 50px;
      font-weight: 600;
      text-decoration: none;
      box-shadow: 0 6px 20px rgba(37, 211, 102, 0.7);
      transition: background 0.3s ease;
    }
    
    .btn-whatsapp:hover {
      background: #1ebe5d;
      box-shadow: 0 8px 25px rgba(27, 190, 93, 1);
    }
    
    .btn-whatsapp svg {
      margin-right: 12px;
      width: 24px;
      height: 24px;
      fill: #fff;
    }
    
    footer {
      margin-top: 50px;
      font-size: 0.9rem;
      color: #ccc;
      text-align: center;
    }
    
  </style>
</head>
<body>
  <header>
    <h1>IPTV Premium</h1>
    <p>Teste nosso plano por 6 horas - Garantia de qualidade!</p>
  </header>
  
  <main>
    <div class="plan" role="button" tabindex="0" aria-label="Comprar plano teste de 6 horas via WhatsApp">
      <h2>Plano Teste</h2>
      <p>6 horas de acesso completo</p>
      <div class="price">R$ 5,00</div>
      <a 
        href="http://wa.me/5519971672016?text=Olá!%20Gostaria%20de%20adquirir%20o%20plano%20teste%20de%206%20horas%20de%20IPTV." 
        target="_blank" 
        rel="noopener noreferrer" 
        class="btn-whatsapp"
        aria-label="Entrar em contato via WhatsApp"
      >
        <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" aria-hidden="true" focusable="false">
          <path d="M20.52 3.48a11.72 11.72 0 0 0-16.55 0c-4.59 4.59-4.6 12.06 0 16.66l-2.37 5.98 6.11-2.31c4.59 2.8 11.2 1.7 15.39-3.5 4.59-4.6 4.6-12.06 0-16.66zm-7.06 15.58c-2.67 0-5.12-1.37-6.47-3.63l-.46-.76-3.43 1.3 1.37-3.35-.48-.75a6.47 6.47 0 0 1 3.47-10.48c3.59 0 6.51 2.93 6.51 6.53 0 3.6-2.92 6.54-6.52 6.54zm3.28-5.6c-.18-.09-1.07-.52-1.24-.58-.17-.07-.29-.1-.41.09-.11.18-.42.58-.51.7-.09.11-.17.13-.35.04-.18-.1-.76-.28-1.45-.9-.54-.48-.9-1.07-1.01-1.25-.1-.18-.01-.28.08-.37.08-.08.18-.19.27-.28.09-.09.12-.16.18-.27.06-.1.03-.19-.01-.28-.05-.09-.41-1-0.57-1.38-.15-.37-.31-.32-.41-.33-.11-.01-.23-.01-.36-.01-.12 0-.31.04-.47.19-.16.16-.63.62-.63 1.52 0 .9.65 1.77.74 1.9.09.13 1.27 1.94 3.08 2.72.43.19.76.3 1.02.39.43.15.82.13 1.13.08.34-.06 1.07-.44 1.22-.86.14-.43.14-.79.1-.86-.05-.06-.18-.09-.36-.18z"/>
        </svg>
        Comprar no WhatsApp
      </a>
    </div>
  </main>
  
  <footer>
    &copy; 2025 IPTV Premium - Todos os direitos reservados.
  </footer>
</body>
</html>
