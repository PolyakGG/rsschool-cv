# Sergey Polyakov

## Contacts 
Telegram: https://t.me/PolyakGG
Discord: polyakgg

## About me

I'm 25, I play for a living. The goal is to find a job in the IT industry.

## Skills 

 I know a little python, golang, js.

 ## Code Examples
```
package service

import (
	"errors"
	"pastebin-go/internal/models"
	"pastebin-go/internal/repository"
)

type PasteService struct { // ссылаемся на файл repository/sqlite.go
	Repo *repository.PasteRepository
}

func NewPasteService(repo *repository.PasteRepository) *PasteService { // Указатель для того чтобы структура не попал в кучу
	return &PasteService{Repo: repo}
}

func (s *PasteService) CreatePaste(title, content string) (int, error) {
	paste := &models.Paste{
		Title:   title,
		Content: content,
	}
	return s.Repo.Create(paste)
}

func (s *PasteService) GetPaste(id int) (*models.Paste, error) {
	return s.Repo.GetById(id)
}

/*
Функция GetAll необходима для правильной организации кода и разделения ответственности.
Она предоставляет удобный интерфейс для получения всех паст из базы данных через сервисный слой,
позволяя контроллерам (хэндлерам) не заниматься непосредственно запросами к базе данных.
*/

func (s *PasteService) GetAll() ([]models.Paste, error) {
	return s.Repo.GetAll()
}

// Метод для получения пасты по ID
func (s *PasteService) GetPasteByID(id string) (*models.Paste, error) {
	paste, err := s.Repo.FindByID(id)
	if err != nil {
		return nil, errors.New("paste not found")
	}
	return &paste, nil
}
```
## Projects
an analogue of pastebin on golang,
self-bots for discord for chat parsing
## Experience
There is no commercial development experience

## Languages
Native Language: Russian

English - A2-B1 
I studied a little Spanish, Korean, and now Chinese.

