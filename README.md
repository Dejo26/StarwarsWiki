<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Proyecto Ambiente</title>
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
        <link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.10.16/css/jquery.dataTables.min.css" />
        <script type="text/javascript" src="https://cdn.datatables.net/v/dt/dt-1.10.16/datatables.min.js"></script>
        <style>
            div.dataTables_wrapper {
                width: 800px;
                margin: 0 auto;
            }
        </style>

            <script>
                $(document).ready(function () {
                    var arreglo = ['https://swapi.co/api/people/', 'https://swapi.co/api/people/?page=2', 'https://swapi.co/api/people/?page=3',
                    'https://swapi.co/api/people/?page=4','https://swapi.co/api/people/?page=5', 'https://swapi.co/api/people/?page=6', 'https://swapi.co/api/people/?page=7',
                'https://swapi.co/api/people/?page=8', 'https://swapi.co/api/people/?page=9', 'https://swapi.co/api/planets/'];

                    // asigno a una variable  a un ajax unico que sera ejecutado
                    var call1 = $.ajax({
                        url: arreglo[0]
                    });

                    var call2 = $.ajax({
                        url: arreglo[1]
                    });

                    var call3 = $.ajax({
                        url: arreglo[2]
                    });

                    var call4 = $.ajax({
                        url: arreglo[3]
                    });

                    var call5 = $.ajax({
                        url: arreglo[4]
                    });

                    var call6 = $.ajax({
                        url: arreglo[5]
                    });

                    var call7 = $.ajax({
                        url: arreglo[6]
                    });

                    var call8 = $.ajax({
                        url: arreglo[7]
                    });
                    var call9 = $.ajax({
                        url: arreglo[8]
                    });


                    // ejecuto el when mandandole de momento los dos ajax y espero la respuesta respectiva 
                    // en r1 y r2
                    $.when(call1,call2,call3,call4,call5,call6,call7,call8,call9).done(function (r1,r2,r3,r4,r5,r6,r7,r8,r9) {
                        // la respuesta que devuelve tiene un formato de lista de tres valosres  siendo el primero
                        // el result normal del ajax por eso la data devuelta seria r1[0] en donde entro
                        // al atributo results para ser concatenada con los demas result.




                        data = r1[0].results.concat(r2[0].results.concat(r3[0].results.concat(r4[0].results.concat(r5[0].results.concat(r6[0].results.concat(r7[0].results.concat(r8[0].results.concat(r9[0].results))))))));
                        
                        //var myplanet=JSON.parse(arreglo[10]);


                        $('#example').DataTable({

                            data: data,// aqui inicializo el datatable con la data. 

                            columns: [{data: 'name'},
                                {data: 'height'},
                                {data: 'hair_color'},
                                {data: 'skin_color'},
                                {data: 'gender'}
                                     ]


                        });

                    });
                });


            </script>
    </head>
    <body>
        <div id="table" style="margin: 8px 15%;">
            <table id="example" class="display" style="width:100%">
                <thead>
                    <tr>
                        <th>Nombre</th>
                        <th>Altura</th>
                        <th>Color de Pelo</th>
                        <th>Color de Piel</th>
                        <th>Genero</th>
                        <th>Planeta</th>
                        <th>Filmes</th>
                        <th>Especie</th>
                        <th>Vehiculos</th>
                        <th>Naves</th>
                    </tr>
                </thead>

            </table>
        </div>
    </body>
</html>
