<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SkyWings - Vuelos con 40% de descuento</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Montserrat', sans-serif;
        }
        
        :root {
            --primary-color: #e2001a;
            --secondary-color: #002d72;
            --light-color: #f8f9fa;
            --dark-color: #333;
            --success-color: #28a745;
            --discount-color: #ff6b6b;
        }
        
        body {
            background-color: #f5f7fa;
            color: var(--dark-color);
            line-height: 1.6;
        }
        
        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Header */
        header {
            background-color: white;
            box-shadow: 0 2px 15px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        
        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            color: var(--secondary-color);
            font-weight: 700;
            font-size: 24px;
        }
        
        .logo i {
            color: var(--primary-color);
        }
        
        .main-nav ul {
            display: flex;
            list-style: none;
            gap: 30px;
        }
        
        .main-nav a {
            text-decoration: none;
            color: var(--secondary-color);
            font-weight: 500;
            transition: color 0.3s;
        }
        
        .main-nav a:hover {
            color: var(--primary-color);
        }
        
        .user-actions {
            display: flex;
            gap: 15px;
        }
        
        .btn {
            padding: 8px 20px;
            border-radius: 4px;
            border: none;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .btn-login {
            background-color: transparent;
            color: var(--secondary-color);
            border: 1px solid var(--secondary-color);
        }
        
        .btn-login:hover {
            background-color: var(--secondary-color);
            color: white;
        }
        
        .btn-register {
            background-color: var(--primary-color);
            color: white;
        }
        
        .btn-register:hover {
            background-color: #c10015;
        }
        
        /* Hero Banner */
        .hero {
            background: linear-gradient(rgba(0, 45, 114, 0.85), rgba(226, 0, 26, 0.8)), url('https://images.unsplash.com/photo-1436491865332-7a61a109cc05?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2074&q=80');
            background-size: cover;
            background-position: center;
            color: white;
            padding: 80px 0;
            text-align: center;
            margin-bottom: 40px;
        }
        
        .hero h1 {
            font-size: 42px;
            margin-bottom: 20px;
            font-weight: 700;
        }
        
        .hero p {
            font-size: 20px;
            max-width: 700px;
            margin: 0 auto 30px;
        }
        
        .discount-badge {
            background-color: var(--discount-color);
            color: white;
            padding: 10px 30px;
            border-radius: 50px;
            display: inline-block;
            font-size: 28px;
            font-weight: 700;
            margin-bottom: 30px;
            box-shadow: 0 5px 15px rgba(255, 107, 107, 0.4);
        }
        
        /* Search Form */
        .search-container {
            background-color: white;
            border-radius: 10px;
            padding: 30px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            margin-top: -30px;
            position: relative;
            z-index: 10;
            margin-bottom: 40px;
        }
        
        .search-form {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }
        
        .form-group {
            display: flex;
            flex-direction: column;
        }
        
        .form-group label {
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--secondary-color);
        }
        
        .form-control {
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 16px;
        }
        
        .btn-search {
            background-color: var(--primary-color);
            color: white;
            font-size: 18px;
            padding: 15px;
            align-self: flex-end;
            transition: background-color 0.3s;
        }
        
        .btn-search:hover {
            background-color: #c10015;
        }
        
        /* Flights Section */
        .flights-container {
            margin-bottom: 50px;
        }
        
        .section-title {
            color: var(--secondary-color);
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 2px solid #eee;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .real-time-indicator {
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 14px;
            color: var(--success-color);
        }
        
        .real-time-indicator .pulse {
            width: 10px;
            height: 10px;
            background-color: var(--success-color);
            border-radius: 50%;
            animation: pulse 1.5s infinite;
        }
        
        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.5; }
            100% { opacity: 1; }
        }
        
        .flights-list {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
        
        .flight-card {
            background-color: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 3px 10px rgba(0,0,0,0.08);
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .flight-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.12);
        }
        
        .flight-header {
            background-color: var(--secondary-color);
            color: white;
            padding: 15px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .flight-number {
            font-weight: 600;
        }
        
        .flight-status {
            background-color: var(--success-color);
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 14px;
        }
        
        .flight-body {
            padding: 20px;
            display: grid;
            grid-template-columns: 2fr 1fr 2fr;
            align-items: center;
        }
        
        .flight-origin, .flight-destination {
            text-align: center;
        }
        
        .city {
            font-size: 22px;
            font-weight: 700;
            color: var(--secondary-color);
        }
        
        .time {
            font-size: 28px;
            font-weight: 700;
            margin: 5px 0;
        }
        
        .date {
            color: #666;
            font-size: 14px;
        }
        
        .flight-route {
            text-align: center;
            position: relative;
        }
        
        .flight-route i {
            font-size: 24px;
            color: var(--primary-color);
        }
        
        .duration {
            margin-top: 10px;
            font-weight: 600;
            color: var(--secondary-color);
        }
        
        .flight-price {
            text-align: center;
            padding: 20px;
            background-color: #f9f9f9;
            border-left: 1px solid #eee;
        }
        
        .original-price {
            text-decoration: line-through;
            color: #999;
            font-size: 18px;
            margin-bottom: 5px;
        }
        
        .discount-price {
            color: var(--primary-color);
            font-size: 32px;
            font-weight: 700;
            margin-bottom: 15px;
        }
        
        .discount-tag {
            background-color: var(--discount-color);
            color: white;
            padding: 5px 10px;
            border-radius: 4px;
            font-weight: 600;
            font-size: 14px;
        }
        
        .btn-book {
            background-color: var(--primary-color);
            color: white;
            width: 100%;
            padding: 12px;
            margin-top: 15px;
            font-size: 16px;
            font-weight: 600;
        }
        
        .btn-book:hover {
            background-color: #c10015;
        }
        
        /* Footer */
        footer {
            background-color: var(--secondary-color);
            color: white;
            padding: 50px 0 20px;
        }
        
        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            margin-bottom: 40px;
        }
        
        .footer-column h3 {
            font-size: 18px;
            margin-bottom: 20px;
            color: white;
        }
        
        .footer-column ul {
            list-style: none;
        }
        
        .footer-column ul li {
            margin-bottom: 10px;
        }
        
        .footer-column ul li a {
            color: #ccc;
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .footer-column ul li a:hover {
            color: white;
        }
        
        .footer-bottom {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid rgba(255,255,255,0.1);
            color: #aaa;
            font-size: 14px;
        }
        
        /* Responsive */
        @media (max-width: 992px) {
            .flight-body {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            
            .flight-price {
                border-left: none;
                border-top: 1px solid #eee;
            }
        }
        
        @media (max-width: 768px) {
            .header-container {
                flex-direction: column;
                gap: 15px;
            }
            
            .hero h1 {
                font-size: 32px;
            }
            
            .hero p {
                font-size: 18px;
            }
            
            .discount-badge {
                font-size: 22px;
            }
        }
        
        @media (max-width: 576px) {
            .search-form {
                grid-template-columns: 1fr;
            }
            
            .main-nav ul {
                flex-wrap: wrap;
                justify-content: center;
                gap: 15px;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container header-container">
            <div class="logo">
                <i class="fas fa-plane"></i>
                <span>SkyWings</span>
            </div>
            <nav class="main-nav">
                <ul>
                    <li><a href="#"><i class="fas fa-home"></i> Inicio</a></li>
                    <li><a href="#"><i class="fas fa-search"></i> Buscar Vuelos</a></li>
                    <li><a href="#"><i class="fas fa-suitcase"></i> Mis Viajes</a></li>
                    <li><a href="#"><i class="fas fa-info-circle"></i> Ayuda</a></li>
                </ul>
            </nav>
            <div class="user-actions">
                <button class="btn btn-login">Iniciar Sesión</button>
                <button class="btn btn-register">Registrarse</button>
            </div>
        </div>
    </header>

    <!-- Hero Banner -->
    <section class="hero">
        <div class="container">
            <div class="discount-badge">¡40% DE DESCUENTO EN TODOS LOS VUELOS!</div>
            <h1>Vuela a tu destino soñado</h1>
            <p>Encuentra las mejores ofertas en vuelos nacionales e internacionales. Todos nuestros precios ya incluyen un 40% de descuento aplicado.</p>
        </div>
    </section>

    <!-- Search Form -->
    <div class="container">
        <div class="search-container">
            <h2 style="color: var(--secondary-color); margin-bottom: 20px;">Buscar Vuelos</h2>
            <form class="search-form">
                <div class="form-group">
                    <label for="origin">Origen</label>
                    <input type="text" id="origin" class="form-control" placeholder="Ciudad o aeropuerto" value="Bogotá (BOG)">
                </div>
                <div class="form-group">
                    <label for="destination">Destino</label>
                    <input type="text" id="destination" class="form-control" placeholder="Ciudad o aeropuerto" value="Medellín (MDE)">
                </div>
                <div class="form-group">
                    <label for="departure">Fecha de Ida</label>
                    <input type="date" id="departure" class="form-control" value="2023-10-15">
                </div>
                <div class="form-group">
                    <label for="return">Fecha de Regreso</label>
                    <input type="date" id="return" class="form-control" value="2023-10-20">
                </div>
                <div class="form-group">
                    <label for="passengers">Pasajeros</label>
                    <select id="passengers" class="form-control">
                        <option>1 pasajero</option>
                        <option selected>2 pasajeros</option>
                        <option>3 pasajeros</option>
                        <option>4 pasajeros</option>
                    </select>
                </div>
                <button type="submit" class="btn btn-search"><i class="fas fa-search"></i> Buscar Vuelos</button>
            </form>
        </div>
    </div>

    <!-- Flights List -->
    <div class="container flights-container">
        <div class="section-title">
            <h2>Vuelos Disponibles</h2>
            <div class="real-time-indicator">
                <div class="pulse"></div>
                <span>Actualizando en tiempo real</span>
            </div>
        </div>
        
        <div class="flights-list" id="flightsList">
            <!-- Los vuelos se cargarán aquí dinámicamente -->
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>SkyWings</h3>
                    <p>Tu compañía de confianza para viajar por Colombia y el mundo. Ofrecemos las mejores tarifas con descuentos exclusivos.</p>
                </div>
                <div class="footer-column">
                    <h3>Destinos Populares</h3>
                    <ul>
                        <li><a href="#">Bogotá</a></li>
                        <li><a href="#">Medellín</a></li>
                        <li><a href="#">Cartagena</a></li>
                        <li><a href="#">Cali</a></li>
                        <li><a href="#">Miami</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Información</h3>
                    <ul>
                        <li><a href="#">Acerca de nosotros</a></li>
                        <li><a href="#">Contacto</a></li>
                        <li><a href="#">Términos y condiciones</a></li>
                        <li><a href="#">Política de privacidad</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Ayuda</h3>
                    <ul>
                        <li><a href="#">Preguntas frecuentes</a></li>
                        <li><a href="#">Check-in en línea</a></li>
                        <li><a href="#">Estado del vuelo</a></li>
                        <li><a href="#">Cambios y cancelaciones</a></li>
                    </ul>
                </div>
            </div>
            <div class="footer-bottom">
                <p>&copy; 2023 SkyWings. Todos los derechos reservados. Este sitio es una demostración y no está afiliado a Avianca.</p>
            </div>
        </div>
    </footer>

    <script>
        // Datos de vuelos simulados
        const flightsData = [
            {
                id: 1,
                flightNumber: "AV123",
                origin: "Bogotá (BOG)",
                destination: "Medellín (MDE)",
                departureTime: "06:30",
                arrivalTime: "07:30",
                departureDate: "15 Oct 2023",
                arrivalDate: "15 Oct 2023",
                duration: "1h 00m",
                originalPrice: 250000,
                status: "Disponible"
            },
            {
                id: 2,
                flightNumber: "AV456",
                origin: "Bogotá (BOG)",
                destination: "Cartagena (CTG)",
                departureTime: "09:15",
                arrivalTime: "10:45",
                departureDate: "15 Oct 2023",
                arrivalDate: "15 Oct 2023",
                duration: "1h 30m",
                originalPrice: 320000,
                status: "Disponible"
            },
            {
                id: 3,
                flightNumber: "AV789",
                origin: "Bogotá (BOG)",
                destination: "Cali (CLO)",
                departureTime: "14:20",
                arrivalTime: "15:30",
                departureDate: "15 Oct 2023",
                arrivalDate: "15 Oct 2023",
                duration: "1h 10m",
                originalPrice: 280000,
                status: "Disponible"
            },
            {
                id: 4,
                flightNumber: "AV101",
                origin: "Bogotá (BOG)",
                destination: "Miami (MIA)",
                departureTime: "18:00",
                arrivalTime: "23:30",
                departureDate: "15 Oct 2023",
                arrivalDate: "15 Oct 2023",
                duration: "5h 30m",
                originalPrice: 1200000,
                status: "Disponible"
            },
            {
                id: 5,
                flightNumber: "AV202",
                origin: "Bogotá (BOG)",
                destination: "Medellín (MDE)",
                departureTime: "20:45",
                arrivalTime: "21:45",
                departureDate: "15 Oct 2023",
                arrivalDate: "15 Oct 2023",
                duration: "1h 00m",
                originalPrice: 270000,
                status: "Últimos asientos"
            }
        ];

        // Función para aplicar el 40% de descuento
        function applyDiscount(price) {
            return Math.round(price * 0.6);
        }

        // Función para formatear precio en pesos colombianos
        function formatPrice(price) {
            return "$" + price.toLocaleString("es-CO");
        }

        // Función para renderizar los vuelos
        function renderFlights() {
            const flightsList = document.getElementById("flightsList");
            flightsList.innerHTML = "";
            
            flightsData.forEach(flight => {
                const discountedPrice = applyDiscount(flight.originalPrice);
                
                const flightCard = document.createElement("div");
                flightCard.className = "flight-card";
                flightCard.innerHTML = `
                    <div class="flight-header">
                        <div class="flight-number">Vuelo ${flight.flightNumber}</div>
                        <div class="flight-status">${flight.status}</div>
                    </div>
                    <div class="flight-body">
                        <div class="flight-origin">
                            <div class="city">${flight.origin}</div>
                            <div class="time">${flight.departureTime}</div>
                            <div class="date">${flight.departureDate}</div>
                        </div>
                        <div class="flight-route">
                            <i class="fas fa-plane"></i>
                            <div class="duration">${flight.duration}</div>
                        </div>
                        <div class="flight-destination">
                            <div class="city">${flight.destination}</div>
                            <div class="time">${flight.arrivalTime}</div>
                            <div class="date">${flight.arrivalDate}</div>
                        </div>
                    </div>
                    <div class="flight-price">
                        <div class="original-price">${formatPrice(flight.originalPrice)}</div>
                        <div class="discount-price">${formatPrice(discountedPrice)}</div>
                        <div class="discount-tag">40% DE DESCUENTO</div>
                        <button class="btn btn-book" onclick="bookFlight(${flight.id})">Reservar Ahora</button>
                    </div>
                `;
                
                flightsList.appendChild(flightCard);
            });
        }

        // Función para simular actualizaciones en tiempo real
        function simulateRealTimeUpdates() {
            // Cambiar el estado de un vuelo aleatorio cada 10 segundos
            setInterval(() => {
                const randomIndex = Math.floor(Math.random() * flightsData.length);
                const flight = flightsData[randomIndex];
                
                // Alternar entre estados
                if (flight.status === "Disponible") {
                    flight.status = "Últimos asientos";
                } else if (flight.status === "Últimos asientos") {
                    flight.status = "Disponible";
                }
                
                // Actualizar precio original aleatoriamente (simulando fluctuaciones)
                const changePercent = (Math.random() * 0.1) - 0.05; // Entre -5% y +5%
                flight.originalPrice = Math.round(flight.originalPrice * (1 + changePercent));
                
                // Volver a renderizar los vuelos
                renderFlights();
            }, 10000);
        }

        // Función para reservar un vuelo
        function bookFlight(flightId) {
            const flight = flightsData.find(f => f.id === flightId);
            const discountedPrice = applyDiscount(flight.originalPrice);
            alert(`Has seleccionado el vuelo ${flight.flightNumber} de ${flight.origin} a ${flight.destination} por ${formatPrice(discountedPrice)}. Serás redirigido al proceso de pago.`);
        }

        // Inicializar la página
        document.addEventListener("DOMContentLoaded", () => {
            renderFlights();
            simulateRealTimeUpdates();
            
            // Manejar el formulario de búsqueda
            document.querySelector(".search-form").addEventListener("submit", function(e) {
                e.preventDefault();
                const origin = document.getElementById("origin").value;
                const destination = document.getElementById("destination").value;
                
                alert(`Buscando vuelos de ${origin} a ${destination}. En un sistema real, esto cargaría resultados reales.`);
            });
        });
    </script>
</body>
</html>
