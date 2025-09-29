📝 Progreso Semana 2 – Arquitectura Full-Stack (sin React)
🖥️ Frontend (HTML5 + CSS + JS puro)

Tecnologías:

HTML5: estructura de la interfaz.

CSS3: estilos, responsive design.

JavaScript Vanilla: para consumir la API del backend y manejar la interacción.

Objetivo: Proporcionar una UI clara y ligera para que los estudiantes puedan registrarse, iniciar sesión, contestar entrevistas y ver feedback.

Componentes/Páginas principales:

index.html – Pantalla de login/registro.

dashboard.html – Panel del estudiante (botón iniciar entrevista, historial).

interview.html – Pantalla de entrevista tipo chat.

admin.html – Panel del administrador (gestión de preguntas, usuarios, métricas).

Comunicación con Backend:

fetch() con JSON via HTTPS.

Tokens JWT almacenados en cookies o localStorage.

Ventajas:

Fácil despliegue (GitHub Pages, Vercel, Netlify).

No requiere compilación ni frameworks pesados.

🛠️ Backend (Node.js + Express)

Objetivo: Procesar peticiones del frontend, autenticar usuarios, conectar con IA y base de datos.

Endpoints Contemplados:

POST /auth/register – Registro.

POST /auth/login – Inicio de sesión.

POST /interview/start – Iniciar entrevista.

POST /interview/answer – Procesar respuesta y mandar a IA.

GET /history – Consultar historial del estudiante.

GET /admin/metrics – Métricas para admin.

Middleware: Roles (admin/estudiante), autenticación JWT.

🗄️ Base de Datos (MySQL o PostgreSQL)

Tablas iniciales:

Usuarios (con rol admin o estudiante).

Preguntas (temas técnicos, soft skills).

Entrevistas (fecha, user_id, resultados).

Respuestas (respuesta del usuario + feedback IA).

🤖 Servicios Externos (IA)

DeepSeek u OpenAI Chat:

Genera preguntas dinámicas en inglés técnico.

Evalúa las respuestas y devuelve feedback.

🔄 Flujo de datos

Estudiante entra en index.html y se autentica (fetch → backend).

Backend valida credenciales y devuelve token.

Estudiante abre interview.html, presiona “Iniciar Entrevista” → fetch a POST /interview/start.

Backend solicita primera pregunta a la IA y la envía al frontend.

Estudiante responde en el chat → fetch a POST /interview/answer.

Backend envía respuesta del estudiante a IA, recibe feedback y lo devuelve al frontend.

Historial se guarda en base de datos y puede consultarse en dashboard.html.

Admin entra en admin.html para gestionar preguntas, métricas y usuarios.

🔒 Seguridad y Roles

Admin: acceso a panel de métricas y gestión.

Estudiante: acceso solo a su perfil y entrevistas.

HTTPS: cifrado de datos.

CORS: restringir a dominios autorizados.

🌐 Infraestructura recomendada

Frontend (HTML/CSS/JS): GitHub Pages, Vercel o Netlify.

Backend (Node.js): Railway o Render.

Base de datos: PlanetScale, Supabase o Neon.

📊 Resumen de componentes en tabla
Capa	Tecnologías	Función
Frontend	HTML5, CSS3, JavaScript puro	UI de estudiantes y admin, llamadas a la API
Backend	Node.js + Express	API REST, autenticación, lógica de negocio, conexión con IA y DB
Base de Datos	MySQL / PostgreSQL	Persistencia de usuarios, preguntas y entrevistas
Servicios Externos	DeepSeek / OpenAI	Generación de preguntas y feedback en inglés