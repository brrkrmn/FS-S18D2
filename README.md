# SQL Queries
```sql
INSERT INTO tur(ad) VALUES('Biyografi');

INSERT INTO yazar(ad, soyad) VALUES('Nurettin', 'Belek');

UPDATE ogrenci SET sinif = '10C' WHERE sinif = '10B';

UPDATE kitap SET puan = puan + 5;

DELETE FROM yazar WHERE ad = 'Mehmet';

INSERT INTO tur(ad) VALUES('Kişisel Gelişim');

UPDATE kitap SET turno = (
	SELECT turno FROM tur WHERE ad = 'Kişisel Gelişim'
) WHERE ad = 'Benim Üniversitelerim';


CREATE OR REPLACE FUNCTION public.ogrencilistesi()
RETURNS SETOF ogrenci
LANGUAGE 'sql'
AS $BODY$
	SELECT * FROM ogrenci
$BODY$


CREATE PROCEDURE public.ekle(k_ad character varying, k_puan integer, k_yazarno bigint, k_turno bigint)
LANGUAGE 'sql'
AS $BODY$ 
	INSERT INTO public.kitap(ad, puan, yazarno, turno)
	VALUES(k_ad, k_puan, k_yazarno, k_turno)
$BODY$;

CREATE PROCEDURE public.sil(no bigint)
LANGUAGE 'sql'
AS $BODY$ 
	DELETE FROM public.ogrenci WHERE ogrno = no;
$BODY$;
```
