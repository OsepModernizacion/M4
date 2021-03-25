# Configuraciones Generales Meta4 People Net 8

## Ciclo de vida de gestión de personal

Dentro de la empresa, People Net diferencia tres niveles de información: persona, periodo del recurso humano y rol del recurso humano. 

* Cada nivel incluye información del nivel anterior. Para cargar un rol debemos tener un período previamente cargado y para cargar un período debemos tener una persona previamente cargada.
* Una persona puede cargarse en la aplicación como candidato o como periodo del RH (Gestión del Personal | Movimientos de Personal | Alta del Empleado)
* Para un empleado pueden existir muchos períodos 


El módulo Gestión de personal es la base para trabajar con los individuos que mantienen una relación con la empresa. Los datos que se suministran en él, se utilizan en el resto de los módulos funcionales de PeopleNet (Nómina, Formación, Selección, Conocimientos+, etcétera).

Este módulo se relaciona estrechamente con Organización debido a que proporciona el factor humano que intregra la estructura de dicha organización. 

## Definición de Personas

### Mantenimiento de la persona 
Para registrar los datos basicos de una persona debemos completar de manera obligatoria:
* Nombre y Apellidos (1er Apellido obligatorio)
* Fecha de Nacimiento
* Tipo de Documento y número
* CUIL: el sistema valida si el CUIL es correcto, en caso de no serlo informa el error pero deja grabar los cambios de igual manera. 

Datos básicos cargar de una persona:
* Nacionalidad
* Estado Civil 
* Direccion
* Correo electrónico
* Telefono/fax
* Otras formas de contacto
* Datos bancarios
* Documentos 

Información complementaria a cargar:
* Mantenimiento de familiares
* Mantenimineto de CV
* Mantenimiento de la info. medica
* Gestionar Documentos: para la implementación de m4 en OSEP utilizaremos esta opción para cargar la foja de servicio de SIGA, para registrar la transición de ambos sistemas. (Lo historico en SIGA y la nueva implementacion a partir de M4).


## Alta del Empleado

Gestión del Personal | Movimientos de Personal | Alta del Empleado

En función del tipo de contratación que se realice (empleado, empleado externo), la aplicación le
habilitará las opciones que tendrá que cumplimentar y deshabilitará las que no sean específicas
de ese tipo de contratación.

En nuestra implementación eligiremos siempre la opción **EMPLEADO (01)**.

Un empleado, a lo largo de su relación con la organización, puede tener varios periodos de RH.
Si da de alta a un nuevo periodo de RH, es decir a una persona ya contratada, el sistema
generará un nuevo periodo del RH para esa persona. Si desea modificar los datos del periodo
generado, acuda a la opción Mantenimiento del periodo.

* **Definiremos al menos un período por la locación de servicios y un período por la planta (ya sea temporal o permanente) de una persona.**

### Proceso del Alta de un Empleado

***Datos previos al alta***:
* Fecha de alta (fecha en la que el empleado inicia su período)
* Tipo Empleado (siempre 01)
* Tipo Alta: se recomienda usar los tipos de altas creados como parametros, esto permite utilizar plantillas en la carga(trae datos predefinidos por defecto).

Una buena práctica al momento de dar de alta un empleado es revisar si el empleado existe previamente como persona (en Mantenimiento del Rol). Si la persona no existe, colocar la opción **Nueva Alta**. En caso de que la persona exista, buscar por ID RH o número de documento preferentemente y seleccionar la opción **Aceptar**.

Si doy de alta un empleado que ya existía como persona con la opción **Nueva Alta**, el sistema me dejará guardar los cambios pero me saldrá un mensaje informativo de que hay una persona duplicada. Voy a tener dos empleados con distintos ID RHH pero con el mismo CUIL. 


***Datos a cargar en el alta del empleado***

**En datos personales**

* Primer Apellido y nombre de la persona (obligatorio)
* Fecha de Nacimiento (obligatorio)
* Tipo y nº de documento (obligatorio)
* Código del sexo de la persona (obligatorio)
* CUIL (Obligatorio)
* En domicilio (obligatorio): 
    * Codigo de localización (domicilio particular, etc)
    * Calle
    * Pais
* País, provincia, departamento de nacimiento de la persona
* Nacionalidad
* Estado civil
* Apellido de casada
* Telofono fijo y movil
* Correo
* Codigo postal 


**En Organización**
* Empresa: siempre el IDEmpresa empieza con OS (efector donde pertenece el empleado)
* Tipo de rol: siempre tipo **Puesto**
* Puesto de trabajo: siempre el IDPuesto empieza con OS
* Unidad Organizativa: área dentro del organigrama de la organización. Siempre el IDUnidadOrg empieza con OS
* Lugar de trabajo: lugar FISICO de trabajo de la persona, donde está ubicada su oficina. Siempre el ID Lugar de Trabajo empieza con OS
* Cantidad de horas semanales: en el alta del empleado por defecto se selecciona **Ind. tiempo completo (porcentaje de trabajo 100%)**, en caso de que desee modificarlo debe ingresar al **Mantenimiento del Rol**
* Motivo incio: la mayoría de los casos es **Por Resolución** o por **Pase a planta**
* Fecha de antiguedad
* Legajo#Proveedor: para registrar el numero de marcado de un empleado y el numero de proveedor si es contratado. Debe cumplir el siguiente formato nroMarcacion#nroProveedor
* Convenio: regimen salarial
* Categoria: agrupamiento, tramo y subtramo de SIGNOS
* ID Clase
* Tipo Contrato: locacion de servicios, planta temporaria, planta permanente o residentes
* Obra Social: siempre OSEP 
* Datos restantes (zona subsidio, fondo de pension, etc): usar los datos que trae por defecto la plantilla de Tipo de Alta previamente cargada


**En Datos Salariales**
* Frecuencia de pago: siempre mensual
* Tipo de salario: mensualizado
* Modelo/1º Semana: semana de trabajo de la persona, puedo regisrar si posee FULL TIME. Este dato es de suma importancia que sea cargado debido a que es un atributo necesario para realizar la gestión de incidencias de dicho empleado. 

**Nomina**
* Tipo de ajuste: ninguno
* Tipo origen: nómina normal
* ID Moneda: peso argentino
* Tipo Pago: transferencia
* Datos Bancarios:
    * Titular: colocar APELLIDO NOMBRE del empleado (con ese formato en mayusculas)
    * Seleccionar sucursal bancaria en argentina
    * Sucursal bancaria: Banco Nacion
    * Num de Cuenta: si no se tiene los datos de la cuenta del empleado forzar la validación con el siguiente número 999999999
    * CBU: si no se tiene los datos de la cuenta del empleado forzar la validación con el siguiente número 9999999999999999999999
    * Tipo cuenta bancaria: caja de ahorro
    * Moneda: pesos argentinos

## Creación y Mantenimiento de roles de RH
El rol de un empleado es el conjunto de tareas y responsabilidades que conlleva el ejercicio de la actividad profesional en su puesto de trabajo. Por tanto, la definición de un rol supone la
asignación de un puesto a un empleado. Por lo tanto, se establece una relación entre aquel, la
unidad organizativa y lugar de trabajo.

La asignación de un empleado a un puesto de trabajo se realiza por los diferentes procesos de
movimientos de empleados, tales como el alta del empleado o la creación de un nuevo rol.

Inicialmente, cuando se da de alta un empleado, se crea automáticamente un rol principal con el
puesto indicado en el alta. Posteriormente, puede editar información relacionada con este rol.
Un periodo puede tener un rol principal y varios secundarios. Mientras el periodo esté abierto,
siempre debe existir un rol principal. Además, en un periodo no pueden existir dos o más roles
principales de forma simultánea en el tiempo.


### Creacion de un Rol

Gestión de personal | Roles del RH | Mantenimiento del rol

1. Localice la persona deseada con ayuda del filtro y haga clic en el botón Siguiente.
2. Crear un nuevo rol haciendo clic en Nuevo Rol:
    * Registrar de manera obligatoria:
        * Fecha inicio nuevo rol
        * Siempre dejar seleccionado la opción **Puesto**
        * Puesto de trabajo: Siempre empiezan con el ID Puesto = OS*****
        * Unidad Organizativa: Siempre empiezan con el ID Unidad Org = OS*****
        * Cantidad de horas semanales
        * Lugar de trabajo: Siempre empiezan con el ID Lugar Trabajo = OS*****
        * Centro de costo: Siempre colocar **01 Generico**
        * Actividad: Siempre colocar **NAP No Aplica**
    * Registrar de manera opcional:
        * Nombre del rol: en este campo se sugiere colocar la clase y subrogancia de una persona con formato **CLASE XX SUBR. XX**. Por ej, CLASE 12 SUBR. 14
        * Indicación de si el RH se dedica a ese rol a tiempo completo marcando la casilla de verificación Ind. tiempo completo
        * El motivo de cambio de la situación del periodo del RH en la empresa: promoción, recontratación, traslado, nueva contratación, etcétera
3. Guarde los cambios.

##  Baja de Empleados

En las situaciones más frecuentes, se dará de baja al empleado y, con ello, concluirá el proceso. No obstante, al tratarse de un proceso delicado en el caso de que se produjeran errores, PeopleNet permite:
* Si se han producido errores en los datos de la baja (fecha de la baja, motivo, etcétera), modificar dicha información.
* Si los errores se basan en que la baja no es correcta, revertir el proceso de baja, es decir, cancelarla por completo.

La baja supone el cierre o fin del periodo del RH creado a través del proceso Alta del empleado.

El proceso puede ejecutarse para un individuo o para un grupo. Se permite la baja masiva de varios periodos de RH diferentes, siempre que la fecha y motivo de baja sean los mismos. La fecha de baja se utiliza para cerrar el rol principal, los secundarios abiertos y los historiales que tenga asociados el periodo del RH.
Después de consumar el proceso de baja, en el caso de que se necesite volver a contratar al empleado, se ejecutará el proceso Alta del empleado. Debido a que la aplicación ya dispone de los datos sobre el periodo del RH, éstos se pueden recuperar y volver a utilizar sin necesidad de tener que introducirlos.

Gestión de personal | Movimientos de personal | Baja del empleado

1. Indicar la fecha de la baja, esta fecha será utilizada para cerrar el período, el rol y los historiales. 
2. El motivo de la baja.
3. Seleccione el o los RH que desea dar de baja. 
4. Ejecutar baja

### Cancelación o modificación de una baja
PeopleNet permite modificar la información de una baja ejecutada anteriormente. Una vez realizada la baja de un empleado existe la posibilidad de:
* Cancelarla y restablecer todas aquellas situaciones que sean posibles. El proceso de baja no es totalmente reversible, por tanto la situación del empleado en la aplicación puede no ser exactamente igual que en el momento anterior a la ejecución de la baja. Por ejemplo, los registros a futuro que hayan sido borrados no podrán ser recuperados.

Gestión de personal | Movimientos de personal | Cancelar o modificar bajas

* Para cancelar una baja:
    1. Compruebe que el botón de radio Cancelar baja está marcado.
    2. Seleccione el periodo del empleado para el que desee cancelar la baja.
    3. Haga clic en el botón Añadir. El periodo aparece en la parte inferior. Repita estos pasos hasta haber seleccionado todos los periodos para los que quiere cancelar la baja.
    4. Haga clic en el botón Ejecutar proceso. Concluido el proceso de cancelación observe en el registro que tanto la fecha de baja como el motivo de baja están ahora vacíos.

* Para modificar la baja:
    1. Marque el boton de radio modificar baja
    2. Indique la nueva fecha o motivo de baja. La fecha de modificación de la baja tiene que ser mayor o igual a la fecha de baja del periodo.
    3. Seleccione el periodo del empleado para el que desea ejecutar algún cambio en la baja.
    
