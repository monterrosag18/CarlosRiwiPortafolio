# 📧 Formulario de Contacto - Documentación

## Características del Formulario

### ✅ Validación en Tiempo Real
- **Email**: Valida formato correcto (ejemplo@dominio.com)
- **Teléfono**: Valida mínimo 10 dígitos (campo opcional)
- **Mensaje**: Requiere mínimo 10 caracteres
- **Feedback visual**: Borde verde (válido) o rojo (inválido)

### 🎨 Diseño
- **Responsive**: Adaptado para móviles, tablets y desktop
- **Dos columnas**:
  - Izquierda: Información de contacto
  - Derecha: Formulario interactivo
- **Iconos**: Font Awesome para cada campo
- **Colores**: Integrado con la paleta del portafolio

### 📝 Campos del Formulario

1. **Nombre Completo** (requerido)
2. **Correo Electrónico** (requerido)
3. **Teléfono** (opcional)
4. **Asunto** (requerido - selección):
   - Propuesta de Proyecto
   - Colaboración
   - Oportunidad de Empleo
   - Consulta General
   - Otro
5. **Mensaje** (requerido - mínimo 10 caracteres)

### 🔧 Funcionalidades JavaScript

#### Validaciones
```javascript
- validateEmail(): Verifica formato de email
- validatePhone(): Verifica teléfono (opcional, mín. 10 dígitos)
- Validación de longitud de mensaje
```

#### Envío del Formulario
Actualmente el formulario:
1. Valida todos los campos
2. Muestra spinner de "Enviando..."
3. Guarda en localStorage como backup
4. Muestra mensaje de éxito
5. Resetea el formulario

### 🚀 Integración con Backend (Próximo paso)

Para conectar con un backend real, reemplaza la sección de `setTimeout` en `script.js` con:

#### Opción 1: EmailJS (Gratis)
```javascript
emailjs.send("service_id", "template_id", formData)
  .then(response => {
    showMessage('¡Mensaje enviado!', 'success');
  })
  .catch(error => {
    showMessage('Error al enviar', 'error');
  });
```

#### Opción 2: Fetch API a tu servidor
```javascript
fetch('https://tuservidor.com/api/contact', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify(formData)
})
.then(response => response.json())
.then(data => {
  showMessage('¡Mensaje enviado!', 'success');
})
.catch(error => {
  showMessage('Error al enviar', 'error');
});
```

#### Opción 3: Formspree (Simple)
```html
<form action="https://formspree.io/f/TU_FORM_ID" method="POST">
  <!-- tus campos -->
</form>
```

### 📱 Responsive Breakpoints

- **Desktop**: > 991px - 2 columnas
- **Tablet**: 768px - 991px - 2 columnas ajustadas
- **Mobile**: < 767px - 1 columna apilada

### 🎯 Mejoras Futuras

- [ ] Integración con servicio de email real
- [ ] Captcha para prevenir spam
- [ ] Archivo adjunto para CV
- [ ] Calendario para agendar reuniones
- [ ] Chat en vivo
- [ ] Notificaciones por email al administrador

### 💾 Almacenamiento Local

Los mensajes se guardan temporalmente en localStorage:
```javascript
localStorage.getItem('contactMessages')
```

Puedes ver los mensajes en la consola del navegador:
```javascript
console.log(JSON.parse(localStorage.getItem('contactMessages')))
```

### 🎨 Personalización de Estilos

Las variables CSS principales:
```css
--primary: #1e40af;
--secondary: #d97706;
--accent: #0ea5e9;
--dark: #0f172a;
--light: #f8fafc;
```

### ⚡ Performance

- Validación en tiempo real sin afectar rendimiento
- Animaciones suaves con GPU acceleration
- Código optimizado y minificable
- Sin dependencias externas (excepto Font Awesome)

---

**Creado por**: Carlos Monterrosa  
**Fecha**: Diciembre 2025  
**Versión**: 1.0
