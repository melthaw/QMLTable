# QMLTable 2
Based on [QMLTable](https://github.com/spuschhof/QMLTable)

## Goals
Add Pre & Post Column to support complicated operation

PreColumn

* Show row index
* Show radio box 
* Show check box

PostColumn

* Add user defined actions , like Edit Row & Delete Row

## Usage
To use QMLTable, simply add the QML files to your project. A basic table definition could look like this:

    Item {
        Table {
            id: table
            anchors.fill: parent
            model: tableModel
    
            TablePreColumn {
                dataRole: "name"
                headerText: "#"
                columnWidth: 30
                cellDelegate: TableIndexCellDelegate {
                    ...
                }
            }
    
            TableColumn {
                textRole: "name"
                headerText: "Name"
                columnWidth: 200
            }
            TableColumn {
                textRole: "data"
                headerText: "Data"
                columnWidth: table.headerWidth - 200
            }
            
            TablePostColumn {
                dataRole: "name"
                headerText: "Actions"
                columnWidth: 100
                cellDelegate: TableActionCellDelegate {
                    ...
                }
            }
        }
    
        ListModel {
            id: tableModel
            ListElement {
                name: "Entry 1"
                data: "Some Text"
            }
            ListElement {
                name: "Entry 2"
                data: "More Text"
            }
            ListElement {
                name: "Entry 3"
                data: "Even more text"
            }
        }
    }
