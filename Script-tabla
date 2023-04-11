function readOnly() {
	var celdas = document.querySelectorAll('#miTabla td[contenteditable="true"]');
	celdas.forEach(function(celda) {
		celda.setAttribute('contenteditable', 'false');
	});
}

function agregarFila() {
	var miTabla = document.getElementById('miTabla');
	var ultimaFila = miTabla.rows.length;
	var fila = miTabla.insertRow(ultimaFila);
	for (var i = 0; i < miTabla.rows[0].cells.length; i++) {
		var celda = fila.insertCell(i);
		if (ultimaFila < miTabla.rows.length - 1) {
			celda.setAttribute('contenteditable', 'true');
			celda.innerHTML = '';
		} else {
			celda.setAttribute('contenteditable', 'true')
			celda.innerHTML = '';
		}
	}
}

function eliminarFila() {
	var miTabla = document.getElementById('miTabla');
	if (miTabla.rows.length > 2) {
		miTabla.deleteRow(-1);
	} else {
		alert('No se pueden eliminar más filas');
	}
}

function agregarColumna() {
	var miTabla = document.getElementById('miTabla');
	for (var i = 0; i < miTabla.rows.length; i++) {
		if (i == 0) {
			var encabezado = miTabla.rows[i].insertCell(-1);
			encabezado.innerHTML = 'Encabezado ' + (miTabla.rows[0].cells.length + 0);
		} else if (i == miTabla.rows.length - 1) {
			var celda = miTabla.rows[i].insertCell(-1);
			celda.innerHTML = '';
		} else {
			var celda = miTabla.rows[i].insertCell(-1);
			celda.setAttribute('contenteditable', 'true');
			celda.innerHTML = '';
		}
	}
}

function eliminarColumna() {
	var miTabla = document.getElementById('miTabla');
	if (miTabla.rows[0].cells.length > 3) {
		for (var i = 0; i < miTabla.rows.length; i++) {
			miTabla.rows[i].deleteCell(-1);
		}
	} else {
		alert('No se pueden eliminar más columnas');
	}
}


function guardar() {
	// Obtener la tabla y sus celdas
	var miTabla = document.getElementById('miTabla');
	var celdas = miTabla.querySelectorAll('td[contenteditable="true"]');
  
	// Crear un arreglo para almacenar los datos
	var datos = [];
  
	// Recorrer todas las celdas de la tabla
	for (var i = 0; i < celdas.length; i++) {
	  var fila = celdas[i].parentNode.rowIndex;
	  var columna = celdas[i].cellIndex;
	  var contenido = celdas[i].innerHTML;
  
	  // Agregar los datos al arreglo
	  datos.push({
		fila: fila,
		columna: columna,
		contenido: contenido
	  });
	}
  
	// Convertir el arreglo a una cadena JSON
	var datosJSON = JSON.stringify(datos);
  
	// Crear un elemento <a> para descargar la copia de la página
	var enlace = document.createElement('a');
	enlace.innerHTML = 'Descargar copia de la página';
	enlace.addEventListener('click', function() {
	  // Crear un archivo con el contenido de la página y descargarlo
	  var contenido = '<!DOCTYPE html>\n<html>\n<head>\n<title>Tabla1</title>\n</head>\n<body>\n' + document.body.innerHTML + '\n<script>\nvar datos = ' + datosJSON + ';\nfor (var i = 0; i < datos.length; i++) {\nvar fila = datos[i].fila;\nvar columna = datos[i].columna;\nvar contenido = datos[i].contenido;\ndocument.getElementById(\'miTabla\').rows[fila].cells[columna].innerHTML = contenido;\n}\n</script>\n</body>\n</html>';
	  var archivo = new Blob([contenido], { type: 'text/html' });
	  saveAs(archivo, 'tabla1.html');
	});
  
	// Añadir el enlace a la página
	document.body.appendChild(enlace);
  
	// Mostrar un mensaje de confirmación
	alert('Datos guardados correctamente');
  }
  
