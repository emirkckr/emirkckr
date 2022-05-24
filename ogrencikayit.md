#include <stdio.h>
#include <stdlib.h>
struct ogrenci {
	short ogrencino;
	char ad[20];
	char soyad[20];
	char tel[20];
	float notort;
} kayit;

void kayit_ekleme() {
	struct ogrenci kayit;
	FILE *dosya;
	dosya = fopen("notlar.txt", "a");
	printf("Ogrenci No       : "); scanf("%d", &kayit.ogrencino); 
	printf("Ad          : "); scanf("%s", kayit.ad); 
	printf("Soyad       : "); scanf("%s", kayit.soyad); 
	printf("Telefon     : "); scanf("%s", kayit.tel); 
	printf("Not         : "); scanf("%f", &kayit.notort);
	fwrite(&kayit, sizeof(kayit), 1, dosya);
	fclose(dosya);
}
void kayit_listeleme() {
	struct ogrenci kayit;
	FILE *dosya;
	dosya = fopen("notlar.txt", "r");
	printf("ogrenci no  %-15s %-20s %-15s not \n", 
						"Ad", "Soyad", "TelNo");
	while(1) {
		fread(&kayit, sizeof(kayit), 1, dosya);
		if(feof(dosya)) break;
		printf("%5d       %-15s %-20s %-15s %5.2f\n", kayit.ogrencino,
			kayit.ad, kayit.soyad, kayit.tel, kayit.notort);
	}
	fclose(dosya);
}


int main()
{
	
	kayit_ekleme();
	
	kayit_listeleme();
	int x,y;
	printf("Devam Edip Not Eklemek Icin:1\nNot Silmek Icin 2:\nCikmak Icin 3 Basin:\n");
	scanf("%d",&x);
	if(x==1)
	kayit_ekleme();
	if(x==2)
	printf("Ogrenci Numarasi girin:");
	scanf("%d",&y);
	if(x==3)
	return 0;
	
	
}
