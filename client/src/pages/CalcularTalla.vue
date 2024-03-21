<template>
    <div>
        <div class="q-pa-xs text-primary text-h6">
            <q-btn
                flat
                dense
                round
                icon="menu"
                aria-label="Menu"            
            />
            Calculador Tallas
        </div>        
        <q-toolbar>
            <q-btn label="Guardar" flat class="text-capitalize" icon="save" color="primary"/>
            <q-btn label="Procesar" class="text-capitalize" icon="play_arrow" color="green"/>
        </q-toolbar>
        <div class="row q-pa-xs q-col-gutter-xs">        
            <div class="col-4">
                <q-card>
                    <q-card-section class="text-h6 text-primary">
                        Tablas
                    </q-card-section>
                    <q-separator/>
                    <q-card-section>
                        <div class="row q-col-gutter-xs">
                            <div class="col-8">
                                <q-input label="Nombre de tabla" stack-label v-model="nom_tabla"/>
                            </div>
                            <div class="col-3">
                                <q-input label="Tamaño (Mb)"  stack-label v-model="tamano"/>
                            </div>
                            <div class="col q-pt-md">
                                <q-btn icon="add" flat rounded color="primary" @click="add_tabla"></q-btn>
                            </div>
                        </div>
                    </q-card-section>
                    <q-table
                    :rows="rows"
                    :columns="columns"
                    separator="vertical"
                    dense
                    :pagination="pagination"
                    row-key="name"
                    >

                    </q-table>
                </q-card>
            </div>
            <div class="col-4">
                <q-card>
                    <q-card-section class="text-h6 text-primary">
                        Criterios
                    </q-card-section>
                    <q-separator/>
                    <q-card-section>
                        <div class="row q-col-gutter-xs">
                            <div class="col-8">
                                <q-input label="Tamaño de Tablas" v-model="tamano_total_tablas" stack-label readonly/>
                            </div>
                            <div class="col">
                                <q-input label="Nivel" stack-label v-model="nivel_tamano_tablas" readonly/>
                            </div>
                        </div>
                        <div  class="row q-col-gutter-xs">
                            <div class="col-8">
                                <q-input label="Número de Tablas" v-model="numero_total_tablas" stack-label readonly/>
                            </div>
                            <div class="col">
                                <q-input label="Nivel" stack-label v-model="nivel_numero_tablas" readonly/>
                            </div>
                        </div>
                        <div   class="row q-col-gutter-xs">
                            <div class="col-8">
                                <q-input label="Número de consultas/Complejidad" v-model="numero_total_consultas" stack-label readonly></q-input>
                            </div>  
                            <div class="col">
                                <q-input label="Nivel" stack-label v-model="nivel_numero_consultas" readonly/>
                            </div>
                        </div>
                        <div>
                            <q-checkbox                            
                            v-model="flg_oracle_datalake"
                            label="Mueve datos de oracle a datalake"                                                
                            />
                        </div>
                        <div>
                            <q-checkbox                            
                            v-model="flg_coe_dataflow"
                            label="Es un proceso CoE Dataflow"                                                
                            />
                        </div>                        
                    </q-card-section>
                </q-card>
            </div>
            <div class="col-4">
                <q-card>
                    <q-card-section class="text-h6 text-primary">
                        Talla
                    </q-card-section>
                    <q-separator/>
                    <q-card-section>
                        <div class="text-center text-h1">M</div>
                    </q-card-section>
                </q-card>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name:"CalcularTalla",
    data() {
        return {
            nom_tabla:"",
            tamano:"",
            tamano_total_tablas:"300mb",
            numero_total_tablas:"10",
            numero_total_consultas:"50",
            nivel_tamano_tablas:"MEDIO",
            nivel_numero_tablas:"MEDIO",
            nivel_numero_consultas:"MEDIO",
            rows:[],
            pagination:{
                rowsPerPage:20
            },
            columns:[{
                name:"rownum",
                label:"",
                field:"rownum",
                style: 'width: 10px',
            },{
                name:"nom_tabla",
                label:"Nom. Tabla",
                field:"nom_tabla",
                align:"left"
            },{
                name:"tamano",
                label:"Tamaño",
                field:"tamano",
                style:"width:30px;"
            }],
            flg_oracle_datalake:false,
            flg_coe_dataflow:false            
        }
    },
    methods:{
        add_tabla: function(){
            /*
            console.log(this.nom_tabla)
            console.log(this.tamano)
            */
            this.rows.push({
                rownum:"1",
                nom_tabla:this.nom_tabla,
                tamano:this.tamano
            })
        },
        reenum: function(){
            console.log("reenum")
        }
    }
}
</script>