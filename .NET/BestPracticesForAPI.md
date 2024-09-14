# Buenas prácticas en Web API

## Indice

1. [Injección de dependencias](#DependencyInjection)
2. [Principios RESTFul](#RESTFul)
3. [Seguridad, autenticación y autorización](#Security)
4. [Errores](#Errors)
5. [Data Transfer Object](#DTOs)
6. [Versionado](#Versioning)
7. [Cache](#Cache)
8. [Log](#Log)
9. [Validación de datos](#DataValidation)
10. [Paginación y filtrado](#PaginationAndFilter)
11. [Métodos asíncronos](#AsyncMethods)
12. [Documentación](#Documentation)
13. [Referencias](#References)

## Injección de dependencias<a id="DependencyInjection" href="#DependencyInjection" class="anchor"></a>

Reduce el acomplamiento entre componentes.

        public voi ConfigureServices(IServiceCollection services)
        {
            servics.AddScoped<IService, Service>();
        }

## Principios RESTFul<a id="RESTFul" href="#RESTFul" class="anchor"></a>

Usa los códigos de estado HTTP y los verbos de manera correcta.

        [HttpGet("{id}")]
        public async Task<IActionResult> GetUser(int id)
        {
            var user = await _userService.GetUserAsync(id);
            return user == null ? NotFound() : Ok(user);
        }

## Seguridad, autenticación y autorización<a id="Security" href="#Security" class="anchor"></a>

Usa siempre el protocolo seguro HTTPS para encriptar las comunicaciones. Implementa JWT (JSON Web Token) para la autenticación y autorización.

        [Authorize]
        [HttpGet("secure-data")]
        public IActionResult GetSecureData()
        {
            return Ok("This data is secured!");
        }

## Errores<a id="Errors" href="#Errors" class="anchor"></a>

Usa un middleware para administrar los errores no controlados.

        public class ErrorHandlingMiddleware
        {
            public async Task Invoke(HttpContext context, RequestDelegate next)
            {
                try
                {
                    await next(context);
                }
                catch (Exception ex)
                {
                    await HandleExceptionAsync(context, ex);
                }
            }

            private static Task HandleExceptionAsync(HttpContext context, Exception ex)
            {
                context.Response.StatusCode = 500;
                return context.Response.WriteAsync(ex.Message);
            }
        }

## Data Transfer Object<a id="DTOs" href="#DTOs" class="anchor"></a>

Usa DTO's (Data Transfer Object) para transferir la información a procesar.

        public class StudentDto
        {
            public int Id { get; set; }
            public string Name { get; set; }
            public string Surname { get; set; }
        }

## Versionado<a id="Versioning" href="#Versioning" class="anchor"></a>

Versiona las API para mantener retrocompatibilidad y de esta manera, asegurar que no rompas sistemas que esten usando versiones anteriores.

        [ApiVersion("1.0")]
        [Route("api/v{version:apiVersion}/[controller]")]
        public class UsersController : ControllerBase
        {
            [HttpGet]
            public IActionResult GetV1() => Ok("Version 1");
        }

## Cache<a id="Cache" href="#Cache" class="anchor"></a>

Usa la cache para evitar que el servidor se sobrecargue realizando la misma tarea.

        [ResponseCache(Duration = 60)]
        [HttpGet("{id}")]
        public IActionResult GetCachedUser(int id)
        {
            var user = _userService.GetUser(id);
            return Ok(user);
        }

## Log <a id="Log" href="#Log" class="anchor"></a>

Es muy importante saber que es lo que entra y lo que sale de tu API, por lo que necesitarás registrar en un log dicha informaicón. Puedes usar librerias como **[Seriolog](https://serilog.net/)** o **[NLog](https://nlog-project.org/)**.

        public class MyService
        {
            private readonly ILogger<MyService> _logger;

            public MyService(ILogger<MyService> logger)
            {
                _logger = logger;
            }

            public void Process()
            {
                _logger.LogInformation("Processing request at {Time}", DateTime.UtcNow);
            }
        }

## Validación de datos<a id="DataValidation" href="#DataValidation" class="anchor"></a>

Para validar la información que te llega a la API puedes usar herramientas como **Data Annotations** o **Fluent Validation**.

        public class UserDto
        {
            [Required]
            [StringLength(50, MinimumLength = 2)]
            public string Name { get; set; }

            [EmailAddress]
            public string Email { get; set; }
        }

## Paginación y filtrado<a id="PaginationAndFilter" href="#PaginationAndFilter" class="anchor"></a>

Si tienes que realizar una consulta muy grande, tu servidor fallará o te dará un Timeout. Para evitar esto tendrás que paginar la consulta y/o filtrarla. 

        [HttpGet]
        public async Task<IActionResult> GetUsers([FromQuery] int pageNumber = 1, [FromQuery] int pageSize = 10)
        {
            var users = await _userService.GetUsersAsync(pageNumber, pageSize);
            return Ok(users);
        }

## Métodos asíncronos<a id="AsyncMethods" href="#AsyncMethods" class="anchor"></a>

Para mejorar la escalabilidad y la respuesta usa métodos asíncronos.

        public async Task<IActionResult> GetUser(int id)
        {
            var user = await _userService.GetUserByIdAsync(id);
            return Ok(user);
        }

## Documentación<a id="Documentation" href="#Documentation" class="anchor"></a>

Es muy importante documentar la API para que el usuario que vaya a usarla entienda como debe realizar las llamadas a los métodos de la misma. Para ello puedes usar herramientas como **[Swagger](https://swagger.io/)** que te proveen de una página web con los métodos, verbos, parámetros, ...

        public void ConfigureServices(IServiceCollection services)
        {
            services.AddSwaggerGen(c =>
            {
                c.SwaggerDoc("v1", new OpenApiInfo { Title = "My API", Version = "v1" });
            });
        }

        public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
        {
            app.UseSwagger();
            app.UseSwaggerUI(c =>
            {
                c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
            });
        }

### Referencias<a id="References" href="#References" class="anchor"></a>

[Dev.io](https://dev.to/luqman_bolajoko/best-practices-for-building-net-core-web-apis-5hc1)