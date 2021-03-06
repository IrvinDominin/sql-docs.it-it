---
title: Oggetto di partizioni (TMSL) | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ef6371ab2dca177aa02fa04883017c4c90d2c0b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34044125"
---
# <a name="partitions-object-tmsl"></a>Oggetto di partizioni (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Definisce una partizione o logica, nella segmentazione del set di righe di tabella. Una partizione è costituito da una query SQL utilizzata per l'importazione di dati, dati di esempio nell'ambiente di modellazione, o come una query di dati completo per pass-through l'esecuzione di query tramite DirectQuery.  
  
 Come può essere recuperati i dati per la tabella è determinata dalle proprietà della partizione.  Nella gerarchia di oggetti, l'oggetto padre di una partizione è un oggetto table.  
  
## <a name="object-definition"></a>Definizione dell'oggetto  
 Tutti gli oggetti hanno un set comune di proprietà, inclusi nome, tipo, descrizione, una raccolta di proprietà e le annotazioni. **Partizione** oggetti hanno anche le proprietà seguenti.  
  
 Tipo  
 Il tipo di partizione. I valori validi sono di tipo numerici e includono quanto segue:  
  
-   Query (1): dati nella partizione vengono recuperate eseguendo una query su un **DataSource**. Il **DataSource** deve essere un'origine dati definita nel file model.bim.  
  
-   Calcolato (2): dati nella partizione vengono popolati eseguendo un'espressione calcolata.  
  
-   Nessuno (3): in questa partizione di dati viene popolata mediante il push di un set di righe di dati al server come parte dell'operazione di aggiornamento.  
  
 mode  
 Definisce la modalità di query della partizione. I valori validi sono **importare**, **DirectQuery**, o **predefinito** (ereditato). Questo valore è obbligatorio.  
  
|||  
|-|-|  
|**Importa**|Indica a query, le richieste vengono eseguite il motore in memoria analitica l'archiviazione dei dati importati.|  
|**DirectQuery**|Pass-through l'esecuzione di query a un database relazionale esterno. La modalità DirectQuery utilizza partizioni per fornire dati di esempio utilizzati durante la progettazione del modello. Se distribuiti in un server di produzione, è necessario passare alla visualizzazione di dati completo. Tenere presente che la modalità DirectQuery richiede una partizione per ogni tabella e un'origine dati per ogni modello.|  
|**default**|Impostare se si desidera cambiare la modalità più in alto l'albero degli oggetti, a livello di modello o un database. Quando si sceglie l'impostazione predefinita, la modalità query sarà import o DirectQuery.|  
  
 origine  
 Identifica la posizione dei dati da recuperare. I valori validi sono **query, calcolato**, o **Nessuno**. Questo valore è obbligatorio.  
  
|||  
|-|-|  
|**Nessuno**|Utilizzato per la modalità di importazione, in cui i dati vengono caricati e archiviati in memoria.|  
|**query**|Per la modalità DirectQuery, si tratta di una query SQL eseguita nel database relazionale specificato con il modello **DataSource**. Vedere [origini dati oggetto &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md).|  
|**Calcolata**|Le tabelle calcolate vengono originate da un'espressione specificata quando viene creata la tabella. Questa espressione viene considerata l'origine della partizione creata per la tabella calcolata.|  
  
 DataView  
 Per le partizioni DirectQuery, una proprietà aggiuntive dataView ulteriormente specifica se la query che recupera i dati è un campione o set di dati completo. I valori validi sono **completo**, **esempio**, o **predefinito** (ereditato). Come già indicato, esempi vengono utilizzati solo durante il test e modellazione di dati. Vedere [aggiungere dati di esempio per un modello DirectQuery in modalità progettazione](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md) per ulteriori informazioni.  
  
## <a name="usage"></a>Utilizzo  
 Vengono utilizzati oggetti partizione [Alter-comando &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md), [creare comandi &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md), [comando CreateOrReplace &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md), [Eliminare comandi &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md), [comando Refresh &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md), e [comando MergePartitions &#40;&#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md).  
  
 Durante la creazione, la sostituzione o modifica di un oggetto partizione, specificare tutte le proprietà di sola lettura della definizione dell'oggetto. Omissione di una proprietà di lettura / scrittura è considerata un'operazione di eliminazione. Proprietà di lettura / scrittura includono nome, descrizione, la modalità e origine.  
  
## <a name="examples"></a>Esempi  
 **Esempio 1** -una struttura di partizione semplice di una tabella (non una tabella dei fatti).  
  
```  
"partitions": [  
          {  
            "name": "Customer",  
            "source": {  
              "query": "SELECT [dbo].[Customer].* FROM [dbo].[Customer]",  
              "dataSource": "SqlServer localhost FoodmartDB"  
            }  
]  
```  
  
 **Esempio 2** - partizionati i dati delle tabelle dei fatti dipende in genere una clausola WHERE che consente di creare partizioni non sovrapposte per i dati dalla stessa tabella.  
  
```  
"partitions": [  
          {  
            "name": "sales_fact_2015",  
            "source": {  
              "query": "SELECT [dbo].[sales_fact_2015].* FROM [dbo].[sales_fact_2015] WHERE [dbo].[sales_fact_2015].[Quarter]=4",                                                                                          
              "dataSource": "SqlServer localhost FoodmartDB"  
            },  
          }  
        ]  
```  
  
 **Esempio 3** -una tabella calcolata in base a un'espressione DAX.  
  
```  
"partitions": [  
          {  
            "name": "CalcTable1",  
            "source": {  
              "type": "calculated",  
              "expression": "'Product Class'"  
            },  
            }  
]  
```  
  
## <a name="full-syntax"></a>Sintassi completa  
 Di seguito è la rappresentazione dello schema di un oggetto partition.  
  
```  
"partitions": {  
                "type": "array",  
                "items": {  
                  "description": "Partition object of Tabular Object Model (TOM)",  
                  "type": "object",  
                  "properties": {  
                    "name": {  
                      "type": "string"  
                    },  
                    "description": {  
                      "anyOf": [  
                        {  
                          "type": "string"  
                        },  
                        {  
                          "type": "array",  
                          "items": {  
                            "type": "string"  
                          }  
                        }  
                      ]  
                    },  
                    "mode": {  
                      "enum": [  
                        "import",  
                        "directQuery",  
                        "default"  
                      ]  
                    },  
                    "dataView": {  
                      "enum": [  
                        "full",  
                        "sample",  
                        "default"  
                      ]  
                    },  
                    "source": {  
                      "anyOf": [  
                        {  
                          "description": "QueryPartitionSource object of Tabular Object Model (TOM)",  
                          "type": "object",  
                          "properties": {  
                            "type": {  
                              "enum": [  
                                "query",  
                                "calculated",  
                                "none"  
                              ]  
                            },  
                            "query": {  
                              "anyOf": [  
                                {  
                                  "type": "string"  
                                },  
                                {  
                                  "type": "array",  
                                  "items": {  
                                    "type": "string"  
                                  }  
                                }  
                              ]  
                            },  
                            "dataSource": {  
                              "type": "string"  
                            }  
                          },  
                          "additionalProperties": false  
                        },  
                        {  
                          "description": "CalculatedPartitionSource object of Tabular Object Model (TOM)",  
                          "type": "object",  
                          "properties": {  
                            "type": {  
                              "enum": [  
                                "query",  
                                "calculated",  
                                "none"  
                              ]  
                            },  
                            "expression": {  
                              "anyOf": [  
                                {  
                                  "type": "string"  
                                },  
                                {  
                                  "type": "array",  
                                  "items": {  
                                    "type": "string"  
                                  }  
                                }  
                              ]  
                            }  
                          },  
                          "additionalProperties": false  
                        }  
                      ]  
                    },  
                    "annotations": {  
                      "type": "array",  
                      "items": {  
                        "description": "Annotation object of Tabular Object Model (TOM)",  
                        "type": "object",  
                        "properties": {  
                          "name": {  
                            "type": "string"  
                          },  
                          "value": {  
                            "anyOf": [  
                              {  
                                "type": "string"  
                              },  
                              {  
                                "type": "array",  
                                "items": {  
                                  "type": "string"  
                                }  
                              }  
                            ]  
                          }  
                        },  
                        "additionalProperties": false  
                      }  
                    }  
                  },  
                  "additionalProperties": false  
                }  
              },  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento al linguaggio di scripting per modelli tabulari &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
