---
title: Recuperación de datos mediante AdomdDataReader | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- retrieving data
- AdomdDataReader object
- data retrieval [ADOMD.NET], AdomdDataReader object
ms.assetid: 8ed7ea26-b5f8-4852-80fc-75dd62df5b3a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9d3f21807b13b9e3a333ad94b8396d09647cf744
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48196202"
---
# <a name="retrieving-data-using-the-adomddatareader"></a>Recuperar datos mediante AdomdDataReader
  Al recuperar datos analíticos, el objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> proporciona un equilibrio óptimo entre sobrecarga e interactividad. El objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> recupera un flujo de datos de solo lectura, de solo avance y sin información de estructura jerárquica de un origen de datos analíticos. Este flujo de datos no almacenado en búfer habilita la lógica de procedimiento para procesar los resultados de un origen de datos analíticos secuencialmente de forma eficaz. Esto hace que <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> sea una buena opción para recuperar grandes cantidades de datos con fines de visualización, ya que los datos no se almacenan en la memoria caché.  
  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> también puede aumentar el rendimiento de la aplicación al recuperar los datos tan pronto como estén disponibles, en lugar de esperar a que se devuelvan los resultados completos de la consulta. <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> también reduce la sobrecarga del sistema ya que, de forma predeterminada, este lector almacena las filas de una en una en la memoria.  
  
 La contrapartida del rendimiento optimizado es que el objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> proporciona menos información sobre los datos recuperados que otros métodos de recuperación de datos. El objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> no admite un modelo de objetos grande para representar datos o metadatos; además, dicho modelo de objetos tampoco permite características analíticas más complejas, como la reescritura de celdas. Sin embargo, el objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> proporciona un conjunto de métodos con establecimiento inflexible de tipos para recuperar datos de conjuntos de celdas y un método para recuperar metadatos de conjuntos de celdas en formato tabular. Además, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> implementa el **IDbDataReader** interfaz a la compatibilidad con el enlace de datos y para recuperar datos mediante el `SelectCommand` método, desde el **System.Data** espacio de nombres de la Biblioteca de clases de Microsoft .NET Framework.  
  
## <a name="retrieving-data-from-the-adomddatareader"></a>Recuperar datos desde AdomdDataReader  
 Si desea utilizar el objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> para recuperar datos, siga estos pasos:  
  
1.  **Crear una nueva instancia del objeto.**  
  
     Para crear una nueva instancia de la clase <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, llame al método <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> o <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> del objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.  
  
2.  **Recuperar datos.**  
  
     Cuando el comando ejecuta la consulta, ADOMD.NET devuelve los resultados en formato `Resultset` (formato tabular descrito en la especificación de XML for Analysis) a fin de quitar la información de estructura jerárquica de los datos para el objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>. El formato tabular no es muy frecuente en las consultas de datos analíticos debido a la dimensionalidad variable de dichos datos.  
  
     ADOMD.NET almacena estos resultados tabulares en el búfer de red del cliente hasta que los solicite a través de uno de los métodos siguientes:  
  
    -   Llame al método <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Read%2A> del objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>.  
  
         El método <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Read%2A> obtiene una fila de los resultados de la consulta. A continuación, puede pasar el nombre o la referencia ordinal de la columna a la propiedad <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Item%2A> para tener acceso a cada una de las columnas de la fila devuelta. Por ejemplo, la primera columna de la fila actual se denomina ColumnName. A continuación, `reader[0].ToString()` o `reader["ColumnName"].ToString()` devolverá el contenido de la primera columna de la fila actual.  
  
    -   Llame a uno de los métodos de descriptor de acceso con tipo.  
  
         <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> proporciona una serie de métodos de descriptor de acceso con tipo (métodos que permiten tener acceso a los valores de columna con sus tipos de datos nativos). Cuando se conoce el tipo de datos subyacente de un valor de columna, el uso de un método de descriptor de acceso con tipo reduce la conversión de tipos que es necesario realizar al recuperar el valor de columna y, por lo tanto, ofrece el máximo rendimiento.  
  
         Entre los métodos de descriptor de acceso con tipo disponibles se incluyen <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDateTime%2A>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDouble%2A> y <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetInt32%2A>. Para obtener una lista completa de los métodos de descriptor de acceso con tipo, vea <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>.  
  
3.  **Cierre el lector.**  
  
     Siempre se debe llamar al método <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Close%2A> cuando se haya terminado de utilizar el objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>. Mientras haya abierta una instancia de un objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, dicho <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> utiliza <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> de forma exclusiva. No se podrá ejecutar ningún comando en la instancia de <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, ni siquiera para crear otro objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> o `System.Xml.XmlReader`, hasta que se cierre el objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> original.  
  
### <a name="example-of-retrieving-data-from-the-adomddatareader"></a>Ejemplo de recuperación de datos desde AdomdDataReader  
 El ejemplo de código siguiente recorre en iteración un objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> y devuelve los dos primeros valores de cada fila como cadenas.  
  
```vb  
If Reader.HasRows Then  
    Do While objReader.Read()  
        Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _  
            objReader.GetString(0), objReader.GetString(1))  
    Loop  
Else  
  Console.WriteLine("No rows returned.")  
End If  
  
objReader.Close()  
```  
  
```csharp  
if (objReader.HasRows)  
  while (objReader.Read())  
    Console.WriteLine("\t{0}\t{1}", _  
        objReader.GetString(0), objReader.GetString(1));  
else  
  Console.WriteLine("No rows returned.");  
  
objReader.Close();  
```  
  
## <a name="retrieving-metadata-from-the-adomddatareader"></a>Recuperar metadatos desde AdomdDataReader  
 Mientras haya abierta una instancia de un objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, puede recuperar información de esquema, o metadatos, sobre el conjunto de registros actual a través del método <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetSchemaTable%2A>. <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetSchemaTable%2A>Devuelve un `DataTable` objeto que se rellena con la información de esquema para el conjunto de registros actual. `DataTable` contendrá una fila para cada columna del conjunto de registros. Cada columna de la fila de la tabla de esquema se asigna a una propiedad de la columna devuelta en el conjunto de celdas, donde `ColumnName` es el nombre de la propiedad y el valor de la columna es el valor de la propiedad.  
  
### <a name="example-of-retrieving-metadata-from-the-adomddatareader"></a>Ejemplo de recuperación de metadatos desde AdomdDataReader  
 El ejemplo de código siguiente escribe la información de esquema de un objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>.  
  
```vb  
Dim schemaTable As DataTable = objReader.GetSchemaTable()  
  
Dim objRow As DataRow  
Dim objColumn As DataColumn  
  
For Each objRow In schemaTable.Rows  
  For Each objColumn In schemaTable.Columns  
    Console.WriteLine(objColumn.ColumnName & " = " & objRow(objColumn).ToString())  
  Next  
  Console.WriteLine()  
Next  
DataTable schemaTable = objReader.GetSchemaTable();  
```  
  
```csharp  
foreach (DataRow objRow in schemaTable.Rows)  
{  
  foreach (DataColumn objColumn in schemaTable.Columns)  
    Console.WriteLine(objColumn.ColumnName + " = " + objRow[objColumn]);  
  Console.WriteLine();  
}  
```  
  
## <a name="retrieving-multiple-result-sets"></a>Recuperar varios conjuntos de resultados  
 En minería de datos se admite el concepto de tablas anidadas, que ADOMD.NET expone como conjuntos de filas anidados. Para recuperar el conjunto de filas anidado asociado a cada fila, llame al método <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDataReader%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Recuperación de datos de origen de datos analíticos](retrieving-data-from-an-analytical-data-source.md)   
 [Recuperar datos mediante el objeto CellSet](retrieving-data-using-the-cellset.md)   
 [Recuperación de datos mediante XmlReader](retrieving-data-using-the-xmlreader.md)  
  
  
