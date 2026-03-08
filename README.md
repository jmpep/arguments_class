# arguments_class
Python to help creating python with a simple argument interface using argparse
*the argument are predefined in a JSON file ( by default "help.json" )
*you can encode password

## requirement
| library                 | example                               |
|-------------------------|---------------------------------------|
| printoutputdebug_module | from printoutputdebug_module import * |

## how to add remove parameters and define the type of the argument
* the arguments are in the JSON array ( beginning with "arg":[] )
* each lines is an argument
* the types or values are like in argpass
```{"name":..., "default":..., "help":..., "required": ..., "type":....}
````

| Name     | Definition                               |
|----------|------------------------------------------|
| name     | argument tags beginning with '-' or '--' |
| default  | true / false                             |
| help     | help for this command                    |
| required | true / false                             |
| type     | str2bool                                 |
| choices  | ["NORMAL","VERBOSE","DEBUG","SILENT"]    |
| action   | store_true, store_false                  |

## usage 
| library    | example                       |
|------------|-------------------------------|
| parameters | from arguments_class import * |

* set another help file name 
``` args=arguments("myhelp.json")
```

```
    DEFPREFIX=''
    DEFPOSTFIX=''
    DEFINSIDE=''
    args=arguments("help.json",DEFPREFIX,DEFPOSTFIX,DEFINSIDE)
    args.setbase64(args.parameters.base64)  # optional
```
* read a parameter

| Read an argument | Example                                                                                      |
|------------------|----------------------------------------------------------------------------------------------|
| authentication   | args.parameters.authentication                                                               |
| user, password   | user, password, res = args.findUserPassword(args.parameters.user,args.parameters.password)   |
|                  | args.parameters.user=user                                                                    |
|                  | args.parameters.password=password                                                            |
| outputfile       | outputfile=args.parameters.outputfile                                                        |
| action           | action=args.parameters.action                                                                |
|                  | if action=='': action='show-config'                                                          |
| output           | outputjson=args.parameters.json                                                              |
|                  | if outputjson=='': outputjson=outputfile=os.path.join(args.path,args.prog_shortname)+'.json' |
|                  | else: outputjson=args.parameters.json                                                        |
|                  | if folder!='':                                                                               |
|                  | outputjson=os.path.join(folder,outputjson)                                                   |
