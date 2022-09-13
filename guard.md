# guard

1 Crear guard:
      ng g guard guards/nombre-guard
      
2 En ts del guard, agregar:
      constructor(private router:Router){}

      canActivate(
        route: ActivatedRouteSnapshot,
        state: RouterStateSnapshot): Observable<boolean | UrlTree> | Promise<boolean | UrlTree> | boolean | UrlTree {


         // Obtenemos la hora actual
          const hora = new Date().getHours();

        // Comparamos la hora con el máximo permitido
        // Esto sería en caso de que no queremos que
        // pueda entrar a la página después de las 10:00 pm
        console.log(hora);
        if (hora >= 22) {
      
          // Si la hora es mayor o igual redireccionamos al homeComponent
           this.router.navigate(['']);
          // Si devolvemos FALSE no de permitirá el acceso
          return false;
        }

        // Si devolvemos TRUE si se permitirá el acceso.
        return true;
     }

3 Agregamos en el routing-module del home:
         import { AccesoGuard } from '../guards/acceso.guard'; (acceso: nombre del guard)
         
         path:'certificaciones',
         component: CertificacionesComponent,
         canActivate: [AccesoGuard]
         
         
