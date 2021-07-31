# INMET.jl

Julia API to access data from the [Instituto Nacional de Metereologia (INMET)](https://portal.inmet.gov.br).

For more information about the data, please check their [manual](https://portal.inmet.gov.br/manual/manual-de-uso-da-api-esta%C3%A7%C3%B5es) and [viewer](https://mapas.inmet.gov.br).

## Installation

Please install the package with Julia's package manager:

```julia
] add INMET
```

## Usage

Please read the docstrings of the available functions.

Below are a few examples of usage:

```julia
julia> using INMET

julia> INMET.stations()
604×15 DataFrame
 Row │ TP_ESTACAO  CD_ESTACAO  SG_ESTADO  VL_ALTITUDE  CD_SITUACAO  CD_DISTRITO  CD_OSCAR        DT_FIM_OPERACAO  VL_LATITUDE   CD_WSI                   SG_ENTIDADE  DT_INICIO_OPER ⋯
     │ String      String      String     Union…       String       String       Union…          Nothing          String        Union…                   String       String         ⋯
─────┼────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ Automatica  A422        BA         20.93        Pane          04          0-2000-0-86765                   -17.96305555  0-76-0-2906907000000408  INMET        2008-07-20T21: ⋯
   2 │ Automatica  A360        CE         67.15        Pane          03          0-2000-0-81755                   -3.1211111    0-76-0-2300200000000446  INMET        2009-04-21T21:
  ⋮  │     ⋮           ⋮           ⋮           ⋮            ⋮            ⋮             ⋮                ⋮              ⋮                   ⋮                  ⋮                      ⋱
 603 │ Automatica  A247        PA         245          Operante      02          0-2000-0-81896                   -7.110518     0-76-0-1508407000000527  INMET        2016-09-10T21:
 604 │ Automatica  A255        MA         45.5         Operante      02          0-2000-0-81747                   -3.26916666   0-76-0-2114007000000596  INMET        2019-09-17T21:
                                                                                                                                                        4 columns and 600 rows omitted

julia> INMET.series(:A301, Date(2021,1,1), Date(2021,7,31))
212×13 DataFrame
 Row │ VL_LONGITUDE  CD_ESTACAO  UMID_MED  UMID_MIN  TEMP_MIN  UF      TEMP_MED  VL_LATITUDE  CHUVA   VEL_VENTO_MED  TEMP_MAX  DC_NOME  DT_MEDICAO 
     │ String        String      Union…    Union…    Union…    String  Union…    String       Union…  Union…         Union…    String   String     
─────┼─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ -34.95916666  A301        72.5      54        24.3      PE      27.2      -8.05916666  2.8     1.7            31        RECIFE   2021-01-01
   2 │ -34.95916666  A301        72.9      54        22.3      PE      27        -8.05916666  0       1.6            31.6      RECIFE   2021-01-02
  ⋮  │      ⋮            ⋮          ⋮         ⋮         ⋮        ⋮        ⋮           ⋮         ⋮           ⋮           ⋮         ⋮         ⋮
 211 │ -34.95916666  A301        86        61        19.9      PE      23.8      -8.05916666  0       1.1            28.7      RECIFE   2021-07-30
 212 │ -34.95916666  A301                                      PE                -8.05916666  6.6                              RECIFE   2021-07-31
                                                                                                                                   208 rows omitted

julia> INMET.automatic(DateTime(2021,7,1,0))
669×24 DataFrame
 Row │ TEM_INS  PTO_MIN  CD_ESTACAO  TEM_MAX  VL_LONGITUDE  PRE_MIN  PRE_INS  RAD_GLO  UF      VEN_DIR  PTO_INS  VL_LATITUDE   UMD_MAX  HR_MEDICAO  CHUVA   VEN_RAJ  UMD_MIN  TEM_MI ⋯
     │ Union…   Union…   String      Union…   String        Union…   Union…   Union…   String  Union…   Union…   String        Union…   String      Union…  Union…   Union…   Union… ⋯
─────┼────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ 15.4     7.9      A001        15.7     -47.92583332  890.5    890.9    -3.54    DF      160      8        -15.78944444  63       0000        0       3        61       15     ⋯
   2 │ 14.1     4        A002        15.2     -49.220222    937.3    937.7    -3.54    GO      144      4        -16.642841    52       0000        0       2.7      48       14.1
  ⋮  │    ⋮        ⋮         ⋮          ⋮          ⋮           ⋮        ⋮        ⋮       ⋮        ⋮        ⋮          ⋮           ⋮         ⋮         ⋮        ⋮        ⋮        ⋮   ⋱
 668 │ 12                S836        13       -53.3071                        0        PR      135               -23.7503               0000        0       3.7               11.6
 669 │ 5.6               S837        6        -51.067112                      0        PR      0                 -26.233646             0000        0       0.8               4.6
                                                                                                                                                        7 columns and 665 rows omitted
```
