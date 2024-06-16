#include <stdio.h>
#include <stdlib.h>


    //-------------------------------<<GULO NUSCHKAH>>-------------------------------------------
 void menuET(PlisteET *Q , char*cmpt)
 {
	char n[50];PlisteET T1= *Q;int nbr; char cmpt1[10];strcpy(cmpt,"oui");

do{
printf("-------------------------<< Liste des Etudiants >>-------------------------\n");
printf("1- Ajouter des etudiants\n");
printf("2- Supprimer un etudiant de la liste\n");
printf("3- Consulter la liste de tous les etudiants\n");
printf("4- Modifier un etudiant de la liste\n");
printf("5- Retourner au menu principal\n");

printf("--------------------------- <<o>> --------------------------\n\n");
do{
printf("- veuillez choisir le numero la fonction que vous voulez executer: "); gets(n);

} while(n[0]<'1' || n[0]>'5' || n[1]!= '\0') ;

switch (n[0])
  {
    case '1':
       IsertET(&T1);*Q=T1;
       break;
    case '2':
       SupprimerET(&T1);*Q=T1;
       break;
    case '3':
       AfficheET(T1);
       break;
    case '4':
    	ModifierET(&T1);*Q=T1;
       break;
    case '5':
       strcpy(cmpt,"no");
       break;
 }


if(strcmp(cmpt,"no")){
	printf("\n 	//Voulez vous reexecuter le menu de la liste des etudiants? ");
do{
printf("oui ou non? ");
fflush(stdin);
  gets(cmpt1);
} while(strcmp(cmpt1,"oui") && strcmp(cmpt1,"non"));
strcpy(cmpt,cmpt1);
}

   } while(!strcmp(cmpt,"oui"));


}
//------------------------------------------------------------------------------
void menuEP(PlisteEP *Q2,PlisteET *Q1,PlisteOV *Q , char*cmpt) {
	char n[50];int nbr; char cmpt1[10];strcpy(cmpt,"oui");
	PlisteET T1=*Q1; PlisteEP T2=*Q2;PlisteOV T=*Q;

do{
printf("-------------------------<< Liste des Emprunts >>-------------------------\n");
printf("1- Ajouter des emprunts\n");
printf("2- Retourner les emprunts\n");
printf("3- Consulter la liste des emprunts\n");
printf("4- Modifier un emprunt de la liste\n");
printf("5- La duree des emprunts\n");
printf("6- Retourner au menu principal\n");

printf("--------------------------- <<o>> --------------------------\n\n");
do{
printf("- veuillez choisir le numero la fonction que vous voulez executer: "); gets(n);

} while(n[0]<'1' || n[0]>'6' || n[1]!= '\0') ;

switch (n[0])
  {
    case '1':
       AjouterEP(&T2,&T1,&T);*Q1=T1; *Q2=T2;*Q=T;
       break;
    case '2':
       RetournerEP(&T2,&T1); *Q1=T1; *Q2=T2;
       break;
    case '3':
       AfficheEP(T2);
       break;
    case '4':
    	ModifierEP(&T2);*Q1=T1; *Q2=T2;
       break;
    case '5':
      dureeEP ();
       break;
    case '6':
       strcpy(cmpt,"no");
       break;
 }


if(strcmp(cmpt,"no")){
	printf("\n 	//Voulez vous reexecuter le menu de la liste des empruntes ? ");
do{
printf("oui ou non? ");
fflush(stdin);
  gets(cmpt1);
} while(strcmp(cmpt1,"oui") && strcmp(cmpt1,"non"));
strcpy(cmpt,cmpt1);
}

   } while(!strcmp(cmpt,"oui"));


}
//---------------FIN GULO-----------------------
//---------------------------------------------
int main(int argc, char *argv[]) {
  char n[50];char *cmpt=(char*)malloc(10+1);
  PlisteOV T=NULL; PlisteET T1; PlisteEP T2;

  printf("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~<< Bienvenue dans notre programme >>~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n\n");
T=CreerFIFO(); T1=CreerFIFOET(); T2=CreerFIFOEP();
do{

printf("------------------------------- Menu Principal -------------------------------\n");
printf("1- Manipuler la liste des Ouvrages\n");
printf("2- Manipuler la liste des Etudiants\n");
printf("3- Manipuler la liste des Emprunt\n");
printf("4- Consulter la liste des Penalites\n");
printf("------------------------------- <<o>> ------------------------------\n\n");
do{
printf("- veuillez choisir le numero de la liste que vous voulez manipuler: "); gets(n);

} while(n[0]<'1' || n[0]>'4' || n[1]!= '\0') ;

 switch (n[0])
  {
    case '1':
       menuOv(&T,cmpt);
       break;
    case '2':
       menuET(&T1,cmpt);
       break;
    case '3':
       menuEP(&T2,&T1,&T,cmpt);
       break;
    case '4':
    	AffichePN(T1);strcpy(cmpt,"non");
       break;

  }
//*************************************reexecution******************************
if(!strcmp(cmpt,"non")){
	  printf("\n 	//Voulez vous quitter le programme? ");
do{
printf("oui ou non? ");
fflush(stdin);
  gets(cmpt);
} while(strcmp(cmpt,"oui") && strcmp(cmpt,"non"));
}else{
	strcpy(cmpt,"non");
}


 } while(!strcmp(cmpt,"non"));

  printf("\n~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~<< Merci d'avoir utiliser notre programme >>~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n");

    return 0;
}

