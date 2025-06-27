# GM_U3_EXAMEN_PRACTICO

## 1. Resumen Ejecutivo

El presente informe expone los resultados de la auditoría de seguridad realizada sobre el entorno de despliegue de WordPress utilizando Vagrant y Chef. El objetivo fue evaluar la seguridad, configuración, cumplimiento y riesgos asociados a un entorno automatizado de provisionamiento de máquinas virtuales. Se identificaron hallazgos importantes como el uso de credenciales en texto plano, falta de segregación de ambientes y configuraciones de red sin autenticación. Se recomienda mejorar el control de acceso, el manejo de variables sensibles y la implementación de mejores prácticas en infraestructura como código.

## 2. Antecedentes

La auditoría se realizó sobre el proyecto `Chef_Vagrant_Wp`, cuyo propósito es desplegar WordPress utilizando herramientas como Vagrant, Chef, VirtualBox y Ruby. El entorno consta de tres máquinas virtuales:

- **database**: con MySQL  
- **wordpress**: con Apache + WordPress  
- **proxy**: con Nginx  

Este entorno fue desarrollado con fines académicos y de entrenamiento en automatización de despliegue.

## 3. Objetivos de la Auditoría

### Objetivo General:
Evaluar la seguridad y configuración del entorno automatizado de despliegue de WordPress utilizando Vagrant y Chef.

### Objetivos Específicos:

1. Identificar posibles exposiciones de datos sensibles en el entorno.  
2. Revisar la configuración de red y los puertos expuestos.  
3. Evaluar la segregación de ambientes (producción, pruebas).  
4. Analizar el uso de buenas prácticas en recetas Chef.  
5. Verificar la existencia de registros y logs del sistema.

## 4. Normativa y Criterios de Evaluación

- Tecnológico: Infraestructura virtual con Vagrant, configuración de Chef, WordPress, Apache, MySQL y Nginx.  
- Organizacional: No aplica (entorno de pruebas).  
- Normativo: Buenas prácticas de DevOps, ciberseguridad y configuración segura.  
- Periodo auditado: Junio 2025.  
- Áreas evaluadas: Archivos `Vagrantfile`, recetas Chef, archivo `.env` y despliegue final de WordPress.  

La auditoría cubrió el periodo de mayo 2025, evaluando sistemas bajo control directo.

## 5. Metodología y Enfoques

Enfoque basado en riesgos y normativas internacionales:

- **ISO/IEC 27001:2022**  
- **OWASP DevSecOps Guidelines**  
- **Buenas prácticas en Vagrant y Chef**  
- Revisión manual de código  
- Validación operativa y recolección de evidencia  

## 6. Hallazgos y Observaciones

- **Hallazgo 1**: Uso de credenciales en texto plano en `.env` y `Vagrantfile`. ([Anexo D](#11-anexos))  
- **Hallazgo 2**: Falta de segregación de ambientes dev/prod. ([Anexo G](#11-anexos))  
- **Hallazgo 3**: No existen registros de auditoría en `/var/log/`. ([Anexo F](#11-anexos))  
- **Hallazgo 4**: Redes privadas sin autenticación ni firewall. ([Anexo C](#11-anexos))  

## 7. Análisis de Riesgos

| Riesgo                   | Causa (Anexo)              | Impacto | Probabilidad | Nivel de Riesgo |
|--------------------------|----------------------------|---------|--------------|------------------|
| Credenciales sin cifrado | attributes/default.rb (D)  | Alto    | 90%          | Crítico          |
| Puertos sin restricciones| Vagrantfile (C)            | Medio   | 80%          | Alto             |
| Ausencia de segregación  | Recetas Chef (G)           | Medio   | 70%          | Medio            |
| Sin logs de auditoría    | /var/log/ inexistente (F)  | Alto    | 75%          | Alto             |

## 8. Recomendaciones

- Encriptar o manejar de forma segura las credenciales.  
- Establecer entornos separados para desarrollo y producción.  
- Implementar mecanismos de logging y monitoreo.  
- Restringir acceso de red mediante firewall o configuración de Chef.  

## 9. Conclusiones

El entorno cumple su función principal de automatizar el despliegue de WordPress. No obstante, se detectaron vulnerabilidades críticas que deben ser mitigadas para evitar riesgos en producción. Se requiere adoptar medidas correctivas inmediatas para fortalecer la seguridad.

## 10. Comisión Auditora

| Cargo             | Nombre y Apellido       | Rol                      | Planificación | Ejecución | Informe | Total Días |
|-------------------|--------------------------|---------------------------|---------------|-----------|---------|-------------|
| Jefe de Comisión  | Gilmer Mamani Condori    | Est. Ing. Sistemas        | 2 días        | 3 días    | 1 día   | 6 días       |

## 11. Anexos

- **Anexo A**: Captura de `vagrant status`  
- **Anexo B**: Acceso exitoso a http://192.168.56.2/  
- **Anexo C**: Fragmento `Vagrantfile` - redes privadas  
- **Anexo D**: Archivo `.env` con credenciales  
- **Anexo E**: Enlace al repositorio GitHub: [Ver Repositorio](https://github.com/MAMANICONDORIGILMER/GM_U3_EXAMEN_PRACTI)  
- **Anexo F**: Captura de `/var/log/`  
- **Anexo G**: Recetas sin ambientes separados

---

> **Fuente:** Elaboración propia – Proyecto académico en la Universidad Privada de Tacna.