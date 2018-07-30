<template>
  <div class="container">
    <div class="panel panel-default">
      <!-- Default panel contents -->
      <div class="panel-heading">Ingresa una canción</div>
      <div class="panel-body">
        <form>
          <div class="form-group">
            <label>Nombre artista: </label>
            <input type="text" class="form-control" placeholder="Un Artista" v-model="artista"/>
          </div>
          <div class="form-group">
            <label>Nombre canción: </label>
            <input type="text" class="form-control" placeholder="Una Canción" v-model="cancion"/>
          </div>
          <div class="form-group">
            <label for="exampleFormControlSelect2">Pais de origen:</label>
            <select class="form-control" id="exampleFormControlSelect2" v-model="locationPost">
              <option disabled value="">Seleccione un Pais...</option>
              <option v-for="location in locations" :value='location.id'>{{location.nombre}}</option>
            </select>
            <br/>
          </div>
          <div class="form-group">
            <button v-on:click="post" class="btn btn-primary">Ingresa</button>
          </div>
        </form>

      </div>


    </div>
  </div>
</template>

<script>

export default {
  name: 'IngresaCanciones',
  props: {
    msg: String
  },
  data () {
        return {
            artista: '',
            cancion: '',
            locationPost: '',
            locations: [
            {id:1, nombre:"Afghanistan"},
            {id:2, nombre:"Albania"},
            {id:3, nombre:"Algeria"},
            {id:4, nombre:"American Samoa"},
            {id:5, nombre:"Andorra"},
            {id:6, nombre:"Angola"},
            {id:7, nombre:"Anguilla"},
            {id:8, nombre:"Antarctica"},
            {id:9, nombre:"Antigua and Barbuda"},
            {id:10, nombre:"Argentina"},
            {id:11, nombre:"Armenia"},
            {id:12, nombre:"Aruba"},
            {id:13, nombre:"Australia"},
            {id:14, nombre:"Austria"},
            {id:15, nombre:"Azerbaijan"},
            {id:16, nombre:"Bahamas"},
            {id:17, nombre:"Bahrain"},
            {id:18, nombre:"Bangladesh"},
            {id:19, nombre:"Barbados"},
            {id:20, nombre:"Belarus"},
            {id:21, nombre:"Belgium"},
            {id:22, nombre:"Belize"},
            {id:23, nombre:"Benin"},
            {id:24, nombre:"Bermuda"},
            {id:25, nombre:"Bhutan"},
            {id:26, nombre:"Bolivia"},
            {id:27, nombre:"Bosnia and Herzegovina"},
            {id:28, nombre:"Botswana"},
            {id:29, nombre:"Bouvet Island"},
            {id:30, nombre:"Brazil"},
            {id:31, nombre:"British Indian Ocean Territory"},
            {id:32, nombre:"Brunei Darussalam"},
            {id:33, nombre:"Bulgaria"},
            {id:34, nombre:"Burkina Faso"},
            {id:35, nombre:"Burundi"},
            {id:36, nombre:"Cambodia"},
            {id:37, nombre:"Cameroon"},
            {id:38, nombre:"Canada"},
            {id:39, nombre:"Cape Verde"},
            {id:40, nombre:"Cayman Islands"},
            {id:41, nombre:"Central African Republic"},
            {id:42, nombre:"Chad"},
            {id:43, nombre:"Chile"},
            {id:44, nombre:"China"},
            {id:45, nombre:"Christmas Island"},
            {id:46, nombre:"Cocos (Keeling) Islands"},
            {id:47, nombre:"Colombia"},
            {id:48, nombre:"Comoros"},
            {id:49, nombre:"Congo"},
            {id:50, nombre:"Cook Islands"},
            {id:51, nombre:"Costa Rica"},
            {id:52, nombre:"Croatia (Hrvatska)"},
            {id:53, nombre:"Cuba"},
            {id:54, nombre:"Cyprus"},
            {id:55, nombre:"Czech Republic"},
            {id:56, nombre:"Denmark"},
            {id:57, nombre:"Djibouti"},
            {id:58, nombre:"Dominica"},
            {id:59, nombre:"Dominican Republic"},
            {id:60, nombre:"East Timor"},
            {id:61, nombre:"Ecuador"},
            {id:62, nombre:"Egypt"},
            {id:63, nombre:"El Salvador"},
            {id:64, nombre:"Equatorial Guinea"},
            {id:65, nombre:"Eritrea"},
            {id:66, nombre:"Estonia"},
            {id:67, nombre:"Ethiopia"},
            {id:68, nombre:"Falkland Islands (Malvinas)"},
            {id:69, nombre:"Faroe Islands"},
            {id:70, nombre:"Fiji"},
            {id:71, nombre:"Finland"},
            {id:72, nombre:"France"},
            {id:73, nombre:"France Metropolitan"},
            {id:74, nombre:"French Guiana"},
            {id:75, nombre:"French Polynesia"},
            {id:76, nombre:"French Southern Territories"},
            {id:77, nombre:"Gabon"},
            {id:78, nombre:"Gambia"},
            {id:79, nombre:"Georgia"},
            {id:80, nombre:"Germany"},
            {id:81, nombre:"Ghana"},
            {id:82, nombre:"Gibraltar"},
            {id:83, nombre:"Guernsey"},
            {id:84, nombre:"Greece"},
            {id:85, nombre:"Greenland"},
            {id:86, nombre:"Grenada"},
            {id:87, nombre:"Guadeloupe"},
            {id:88, nombre:"Guam"},
            {id:89, nombre:"Guatemala"},
            {id:90, nombre:"Guinea"},
            {id:91, nombre:"Guinea-Bissau"},
            {id:92, nombre:"Guyana"},
            {id:93, nombre:"Haiti"},
            {id:94, nombre:"Heard and Mc Donald Islands"},
            {id:95, nombre:"Honduras"},
            {id:96, nombre:"Hong Kong"},
            {id:97, nombre:"Hungary"},
            {id:98, nombre:"Iceland"},
            {id:99, nombre:"India"},
            {id:100, nombre:"Isle of Man"},
            {id:101, nombre:"Indonesia"},
            {id:102, nombre:"Iran (Islamic Republic of)"},
            {id:103, nombre:"Iraq"},
            {id:104, nombre:"Ireland"},
            {id:105, nombre:"Israel"},
            {id:106, nombre:"Italy"},
            {id:107, nombre:"Ivory Coast"},
            {id:108, nombre:"Jersey"},
            {id:109, nombre:"Jamaica"},
            {id:110, nombre:"Japan"},
            {id:111, nombre:"Jordan"},
            {id:112, nombre:"Kazakhstan"},
            {id:113, nombre:"Kenya"},
            {id:114, nombre:"Kiribati"},
            {id:115, nombre:"Korea Democratic Peoples Republic of"},
            {id:116, nombre:"Korea Republic of"},
            {id:117, nombre:"Kosovo"},
            {id:118, nombre:"Kuwait"},
            {id:119, nombre:"Kyrgyzstan"},
            {id:120, nombre:"Lao Peoples Democratic Republic"},
            {id:121, nombre:"Latvia"},
            {id:122, nombre:"Lebanon"},
            {id:123, nombre:"Lesotho"},
            {id:124, nombre:"Liberia"},
            {id:125, nombre:"Libyan Arab Jamahiriya"},
            {id:126, nombre:"Liechtenstein"},
            {id:127, nombre:"Lithuania"},
            {id:128, nombre:"Luxembourg"},
            {id:129, nombre:"Macau"},
            {id:130, nombre:"Macedonia"},
            {id:131, nombre:"Madagascar"},
            {id:132, nombre:"Malawi"},
            {id:133, nombre:"Malaysia"},
            {id:134, nombre:"Maldives"},
            {id:135, nombre:"Mali"},
            {id:136, nombre:"Malta"},
            {id:137, nombre:"Marshall Islands"},
            {id:138, nombre:"Martinique"},
            {id:139, nombre:"Mauritania"},
            {id:140, nombre:"Mauritius"},
            {id:141, nombre:"Mayotte"},
            {id:142, nombre:"Mexico"},
            {id:143, nombre:"Micronesia Federated States of"},
            {id:144, nombre:"Moldova Republic of"},
            {id:145, nombre:"Monaco"},
            {id:146, nombre:"Mongolia"},
            {id:147, nombre:"Montenegro"},
            {id:148, nombre:"Montserrat"},
            {id:149, nombre:"Morocco"},
            {id:150, nombre:"Mozambique"},
            {id:151, nombre:"Myanmar"},
            {id:152, nombre:"Namibia"},
            {id:153, nombre:"Nauru"},
            {id:154, nombre:"Nepal"},
            {id:155, nombre:"Netherlands"},
            {id:156, nombre:"Netherlands Antilles"},
            {id:157, nombre:"New Caledonia"},
            {id:158, nombre:"New Zealand"},
            {id:159, nombre:"Nicaragua"},
            {id:160, nombre:"Niger"},
            {id:161, nombre:"Nigeria"},
            {id:162, nombre:"Niue"},
            {id:163, nombre:"Norfolk Island"},
            {id:164, nombre:"Northern Mariana Islands"},
            {id:165, nombre:"Norway"},
            {id:166, nombre:"Oman"},
            {id:167, nombre:"Pakistan"},
            {id:168, nombre:"Palau"},
            {id:169, nombre:"Palestine"},
            {id:170, nombre:"Panama"},
            {id:171, nombre:"Papua New Guinea"},
            {id:172, nombre:"Paraguay"},
            {id:173, nombre:"Peru"},
            {id:174, nombre:"Philippines"},
            {id:175, nombre:"Pitcairn"},
            {id:176, nombre:"Poland"},
            {id:177, nombre:"Portugal"},
            {id:178, nombre:"Puerto Rico"},
            {id:179, nombre:"Qatar"},
            {id:180, nombre:"Reunion"},
            {id:181, nombre:"Romania"},
            {id:182, nombre:"Russian Federation"},
            {id:183, nombre:"Rwanda"},
            {id:184, nombre:"Saint Kitts and Nevis"},
            {id:185, nombre:"Saint Lucia"},
            {id:186, nombre:"Saint Vincent and the Grenadines"},
            {id:187, nombre:"Samoa"},
            {id:188, nombre:"San Marino"},
            {id:189, nombre:"Sao Tome and Principe"},
            {id:190, nombre:"Saudi Arabia"},
            {id:191, nombre:"Senegal"},
            {id:192, nombre:"Serbia"},
            {id:193, nombre:"Seychelles"},
            {id:194, nombre:"Sierra Leone"},
            {id:195, nombre:"Singapore"},
            {id:196, nombre:"Slovakia"},
            {id:197, nombre:"Slovenia"},
            {id:198, nombre:"Solomon Islands"},
            {id:199, nombre:"Somalia"},
            {id:200, nombre:"South Africa"},
            {id:201, nombre:"South Georgia South Sandwich Islands"},
            {id:202, nombre:"Spain"},
            {id:203, nombre:"Sri Lanka"},
            {id:204, nombre:"St. Helena"},
            {id:205, nombre:"St. Pierre and Miquelon"},
            {id:206, nombre:"Sudan"},
            {id:207, nombre:"Suriname"},
            {id:208, nombre:"Svalbard and Jan Mayen Islands"},
            {id:209, nombre:"Swaziland"},
            {id:210, nombre:"Sweden"},
            {id:211, nombre:"Switzerland"},
            {id:212, nombre:"Syrian Arab Republic"},
            {id:213, nombre:"Taiwan"},
            {id:214, nombre:"Tajikistan"},
            {id:215, nombre:"Tanzania United Republic of"},
            {id:216, nombre:"Thailand"},
            {id:217, nombre:"Togo"},
            {id:218, nombre:"Tokelau"},
            {id:219, nombre:"Tonga"},
            {id:220, nombre:"Trinidad and Tobago"},
            {id:221, nombre:"Tunisia"},
            {id:222, nombre:"Turkey"},
            {id:223, nombre:"Turkmenistan"},
            {id:224, nombre:"Turks and Caicos Islands"},
            {id:225, nombre:"Tuvalu"},
            {id:226, nombre:"Uganda"},
            {id:227, nombre:"Ukraine"},
            {id:228, nombre:"United Arab Emirates"},
            {id:229, nombre:"United Kingdom"},
            {id:230, nombre:"United States"},
            {id:231, nombre:"United States minor outlying islands"},
            {id:232, nombre:"Uruguay"},
            {id:233, nombre:"Uzbekistan"},
            {id:234, nombre:"Vanuatu"},
            {id:235, nombre:"Vatican City State"},
            {id:236, nombre:"Venezuela"},
            {id:237, nombre:"Vietnam"},
            {id:238, nombre:"Virgin Islands (British)"},
            {id:239, nombre:"Virgin Islands (U.S.)"},
            {id:240, nombre:"Wallis and Futuna Islands"},
            {id:241, nombre:"Western Sahara"},
            {id:242, nombre:"Yemen"},
            {id:243, nombre:"Zaire"},
            {id:244, nombre:"Zambia"},
            {id:245, nombre:"Zimbabwe"}
            ]
                }
    },
  methods: {
    post: function(){
      if(this.artista == '' || this.cancion == ''){
          alert('Todos los campos deben ser ingresados');
      }
      else{
        this.$http.post('http://localhost:3000/song/', {
                "name": this.artista + " - " + this.cancion,
                "location_id": this.locationPost
            }).then(response => {
                this.artista = '';
                this.cancion = '';
                this.locationPost = '';
                console.log(response);
                alert('Se ha ingresado correctamente la canción ' + response.body.name);
            }, response => {
                console.log(response);
                alert('Error, sin conexión');
        });
      }
    }
  }
}
</script>